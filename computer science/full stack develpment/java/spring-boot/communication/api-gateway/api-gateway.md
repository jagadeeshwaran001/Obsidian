This is a single entry point for all our [[Microservice]], This is also called as [[Edge server]].

1. First add the spring-cloud-gateway dependency to the project and import.
2. We can give the [[spring boot config server]]'s configuration.
3. We also can give the [[Eureka server]]'s configuration if available (If we use Euraka server, Then its possible to invoke the service with all Capital letter(Name of the service registered in the [[Eureka server]])).
4. We need to specify the below property to enable the [[api-gateway routing]].
eg:
```yaml
cloud:
    gateway:
      discovery:
        locator:
          enabled: true
          lowerCaseServiceId: true
```

>We can able to see the [[actuator endpoints]] related to [[api-gateway]] in `host:port/actuator/gateway/routes`

> lowerCaseServiceId to call a service with the lowercase instead of the uppercase [[Eureka server]] name. But still it needs to match the spelling with [[service registry]].


## Customizing the Routing.

We need to create a [[Configuration Bean]] to customize the routing.

If we create a custom routing using [[Configuration Bean]] then we can disable the default auto configuration like the below:
```yaml
cloud:
    gateway:
      discovery:
        locator:
          enabled: false
```


```java
@Bean
	public RouteLocator eazyBankRouteConfig(RouteLocatorBuilder routeLocatorBuilder) {
		return routeLocatorBuilder.routes()
						.route(p -> p
								.path("/eazybank/accounts/**")
								.filters( f -> f.rewritePath("/eazybank/accounts/(?<segment>.*)","/${segment}")
										.addResponseHeader("X-Response-Time", LocalDateTime.now().toString()))
								.uri("lb://ACCOUNTS"))
					.route(p -> p
							.path("/eazybank/loans/**")
							.filters( f -> f.rewritePath("/eazybank/loans/(?<segment>.*)","/${segment}")
									.addResponseHeader("X-Response-Time", LocalDateTime.now().toString()))
							.uri("lb://LOANS"))
					.route(p -> p
							.path("/eazybank/cards/**")
							.filters( f -> f.rewritePath("/eazybank/cards/(?<segment>.*)","/${segment}")
									.addResponseHeader("X-Response-Time", LocalDateTime.now().toString()))
							.uri("lb://CARDS")).build();


	}
```