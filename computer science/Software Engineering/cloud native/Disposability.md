In [[Microservice]] architecture we cannot manually watch all the up state of the all microservice.
If any of the microservice went down because of the overload of something, then we need to gracefully kill or expand those service, do [[horizontal scaling]] and [[load balance]] the microservice.

The one way to achieve is using the [[Kubernetes]].