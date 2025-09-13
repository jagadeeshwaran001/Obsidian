We can handle a global exception in a separate class, We need to annotate that class with the 
[[spring-annotation]] `@ControllerAdvice` 

For Each Exception we need to mention write a separate method with the [[spring-annotation]] `@ExceptionHandler` 

We can mention the `@ResponseStatus(value = HttpStatus.BAD_REQUEST)` in the [[custom Exception]] we created to send the status of the request.

eg:

```java
@ControllerAdvice  
public class GlobalExceptionHandler{  
  
    @ExceptionHandler(Exception.class)  
    public ResponseEntity<ErrorResponseDto> handleGlobalException(Exception exception, WebRequest webRequest) {  
        ErrorResponseDto errorResponseDTO = new ErrorResponseDto(  
                webRequest.getDescription(false),  
                HttpStatus.INTERNAL_SERVER_ERROR,  
                exception.getMessage(),  
                LocalDateTime.now()  
        );  
        return new ResponseEntity<>(errorResponseDTO, HttpStatus.INTERNAL_SERVER_ERROR);  
    }
    
@ExceptionHandler(CustomAlreadyExistsException.class)  
public ResponseEntity<ErrorResponseDto> handleCustomAlreadyExistsException(CustomAlreadyExistsException exception, WebRequest webRequest) {  
    ErrorResponseDto errorResponseDto = new ErrorResponseDto(  
            webRequest.getDescription(false),  
            HttpStatus.BAD_REQUEST,  
            exception.getMessage(),  
            LocalDateTime.now()  
            );  
  
    return new ResponseEntity<>(errorResponseDto, HttpStatus.BAD_REQUEST);  
}
```