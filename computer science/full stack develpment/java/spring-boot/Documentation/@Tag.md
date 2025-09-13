This [[swagger-annotation]] is used to mention the name and description of the specific [[spring-controller]] for [[Swagger open-api]].

```java
@Tag(
        name = "CRUD REST APIs for Accounts in EazyBank",
        description = "CRUD REST APIs in EazyBank to CREATE, UPDATE, FETCH AND DELETE account details"
)
public class AccountsController {}
```