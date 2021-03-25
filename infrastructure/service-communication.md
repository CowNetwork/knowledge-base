# Service Communication

There are two means of communication covered by this document:

* Request/Response (one to one)
* Multicast/Broadcast (one to many)

To achieve the best of both worlds, we are using a combination of [gRPC](https://grpc.io/) for targeted api requests and [Kafka](https://kafka.apache.org/) with [Protocol Buffers](https://developers.google.com/protocol-buffers) for event/message broadcasting.

![](https://i.imgur.com/7BBMAcy.png)

Linkerd (https://linkerd.io/) will handle retry and timeout logic for gRPC requests. This will allows us to restart services in production while the proxy will cache the requests issued during the downtime, just as Kafka does for broadcasts.
