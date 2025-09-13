My simpley add the dependency below we can have the [[API documentation]] in [[Spring]] application.

```xml
<dependency>  
    <groupId>org.springdoc</groupId>  
    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>  
    <version>2.8.13</version>  
</dependency>
```

>After this we can able to see out api documentation in the url `http://localhost:8983/swagger-ui/index.html`


If we need to customize the documentation then: 

```java
@OpenAPIDefinition(  
        info = @Info(  
                title = "Accounts microservice REST API Documentation",  
                description = "EazyBank Accounts microservice REST API docs",  
                version = "v1",  
                contact = @Contact(  
                        name = "Madan Reddy",  
                        email = "tutor@eazybytes.com",  
                        url = "https://www.eazybytes.com"  
                ),  
                license = @License(  
                        name = "Apache 2.0",  
                        url = "https://www.eazybytes.com"  
                )  
        ),  
        externalDocs = @ExternalDocumentation(  
                description =  "EazyBank Accounts microservice REST API docs",  
                url = "https://www.eazybytes.com/swagger-ui.html"  
        )  
)  
public class AccountsApplication {  
  
    public static void main(String[] args) {  
       SpringApplication.run(AccountsApplication.class, args);  
    }  
  
}
```
