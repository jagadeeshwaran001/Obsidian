In [[java]] we can able to create a [[custom Exception]] by extending the class Either [[RunTimeException]] or [[Exception]].

> The Exception extends the class [[Throwable]], But it is not recommended to extend and create a custom exception by extending the [[Throwable]] class.

eg:

```java
@ResponseStatus(value = HttpStatus.BAD_REQUEST)  
public class CustomAlreadyExistsException extends RuntimeException{  
  
    public CustomAlreadyExistsException(String message) {  
        super(message);  
    }  
}
```

> See the backlink for **ResponseStatus** information.