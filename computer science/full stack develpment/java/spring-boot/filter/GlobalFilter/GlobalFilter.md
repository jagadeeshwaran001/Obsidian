We can able to implement the [[GlobalFilter]] by 

implementing the [[GlobalFilter]] interface and defined the abstract method.

eg:

```java
@Order(1)
@Component
public class RequestTraceFilter implements GlobalFilter {
	@Override
	public Mono<Void> filter(ServerWebExchange exchange, GatewayFilterChain chain){
		//implementation
    }
}
```


>The [[@order]] is used to specify the order of [[GlobalFilter]] execution.

We can Define a [[Configuration Bean]] with the return type [[GlobalFilter]].

eg:

```java
@Configuration
public class ResponseTraceFilter {
	@Bean
    public GlobalFilter postGlobalFilter() {
	    //implementation
    }
}
```