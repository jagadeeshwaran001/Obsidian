- The dependency [[Eureka server]] added project will act as a [[service registry]].
- We need to annotate the [[client side service discovery annotation]] [[@EnableEurekaServer]]
- Then we need to specify the [[application.properties or application.yml]] file for the [[Eureka server]]
eg:
```yaml
server:
  port: 8070

eureka:
  instance:
    hostname: localhost
  client:
    fetchRegistry: false
    registerWithEureka: false
    serviceUrl:
      defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/
```

- now the server changes are completed, we need change the client side code and configuration.
- We need to add the dependency [[Eureka client]] in the client microservice.
- after than we need to add the below confiuration in the [[application.properties or application.yml]] file
eg: 
```yaml
eureka:
  instance:
    preferIpAddress: true
  client:
    fetchRegistry: true
    registerWithEureka: true
    serviceUrl:
      defaultZone: http://${eureka.server.hostname}:${eureka.server.port}/eureka/
info:
  app:
    name: "accounts"
    description: "Eazy Bank Accounts Application"
    version: "1.0.0"
```

>In local we don't have DNS name so we need to user preferIpAddress, so that only it will see for the ip address instead of DNS name.

>The info related configurations are used for [[Eureka Dashboard]], We also need to enable a [[actuators]] endpoint for this under the management. We also need to mention the shoutdown property in the actuators setting for monitoring the client gracefull shoutdown.