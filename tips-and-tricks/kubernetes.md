Kubernetes Tips and Tricks
==========================

Quickly spin up a Pod with a running shell to test stuff
--------------------------------------------------------

```
kubectl run my-shell --rm -i --tty --image ubuntu -- bash
```

Create docker pull secret
-------------------------

```
kubectl create secret docker-registry regcred --docker-server=https://ghcr.io --docker-username=udder-machine --docker-password=password --docker-email=email

# inspect
kubectl get secret regcred --output=yaml
```

Strimzi Operator
----------------

Always use at least 3 replicas of Kafka and ZooKeeper otherwise it will probably not work.

###### tags: `k8s` `ops`