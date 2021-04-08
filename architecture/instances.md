Instances
=========

Step by step sequence when creating an Instance:

```plantuml
@startuml
participant Client
participant Service
participant K8S
participant Controller
participant K8S as second

Client->Service: InstanceCreateRequest
activate Service
Service->K8S: Apply CRD
K8S->Controller: Informs

note left: Steps below happen in parallel
par
        activate Controller
        loop 
            Service->K8S: watch for changes
            activate K8S
            K8S-->Service: updates for instance
            deactivate K8S
        end
        alt State Initializing and IP set
            Service-->Client: InstanceCreatedRequest
        end
    else
        deactivate Service
        Controller->second: Create Pod
        Controller->second: Update Instance with generated ID and state set
        second->Controller: Pod created
        Controller->second: Update Instance with Pod IP set
        deactivate Controller
end
@enduml
```

As shown above the request will only be successfully returned if the `Pod` corresponding to the `Instance` has been scheduled by Kubernetes and received an IP.

###### tags: `architecture`