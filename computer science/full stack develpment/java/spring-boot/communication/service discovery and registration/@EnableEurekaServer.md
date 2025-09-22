This is a [[client side service discovery annotation]] to mark a [[Spring-boot]] application as a [[service registry]].

```java
@SpringBootApplication
@EnableEurekaServer
public class EurekaserverApplication {

	public static void main(String[] args) {
		SpringApplication.run(EurekaserverApplication.class, args);
	}

}
```