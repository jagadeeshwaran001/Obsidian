This type of discovery architecture is where the client is responsible for locating and loadbalancing the other [[Microservice]]s.

Key aspect of [[client side service discovery]]:

1. **service Registration** Client application register themself to the [[service registry]].
2. **Service Discovery** When a client need to communicate the other microservice then it queries the details of the available instance form the [[service registry]].
3. **Load balancing** can be done in client side in this architecture.


Drawback:

It adds more headaches to the [[Developer]]s, where as the [[server side service discovery]] add the headaches to the [[DevOps]] team.

Components used for [[client side service discovery]]:
1. [[spring cloud Netflix Eureka]] - [[service discovery]]
2. [[spring cloud Load Balancer]] - [[client side load balancing]]
3. [[Netflix feign client]].