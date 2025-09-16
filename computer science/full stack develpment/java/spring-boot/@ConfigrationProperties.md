This [[spring-annotation]] is the Recommended way comparing with the [[@Value]] property variable injection.

1. We need to provide a all the variables under one common variable in [[application.properties or application.yml]] file.
2. We need to annotate [[@ConfigrationProperties]](prefix = "common variable") to **entity or record class**
3. Annotate `@EnableConfigurationProperties(value = {entity.class})` in spring Main application.
4. To use the variable in any [[spring-componet]] we need to [[@AutoWire]] the entity class.
eg:

```yml
server:
  port: 8080

accounts:
  message: "Welcome to EazyBank accounts related local APIs "
  contactDetails:
    name: "John Doe - Developer"
    email: "john@eazybank.com"
  onCallSupport:
    - (555) 555-1234
    - (555) 523-1345
```

```java
@ConfigurationProperties(prefix = "accounts")
public record AccountsContactInfoDto(String message, Map<String, String> contactDetails, List<String> onCallSupport) {

}
```

```java
@SpringBootApplication
@EnableConfigurationProperties(value = {AccountsContactInfoDto.class})
public class AccountsApplication {

	public static void main(String[] args) {
		SpringApplication.run(AccountsApplication.class, args);
	}

}
```

```java
@Autowire
private AccountsContactInfoDto accountsContactInfoDto;
```
