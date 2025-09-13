This is used to validate the input data for the [[spring-controller]].

we need to give the validation in both [[spring-controller]] and the [[pojo]] class level.

If we gave the even if we gave the validation to the [[pojo]] class we need to mention the [[spring-annotation]] `@Validated` int he [[spring-controller]]

In the method input of the [[spring-controller]] we need to specify the [[spring-annotation]] `@Valid`

below is the example:

```java
@Validated  
public class AccountsController {
	@PostMapping("/create")  
	public ResponseEntity<ResponseDto> createAccount(@Valid @RequestBody CustomerDto customerDto) {    
	}
	
	@GetMapping("/fetch")  
	public ResponseEntity<CustomerDto> fetchAccountDetails(@RequestParam  
                                                           @Pattern(regexp="(^$|[0-9]{10})",message = "Mobile number must be 10 digits")  String mobileNumber) {
                                                           }
	
}
```

> If we need to throw a [[Global Exception]] if the validation fails we need to extend a  `ResponseEntityExceptionHandler` class and override the method like example given as below


```java
@ControllerAdvice  
public class GlobalExceptionHandler extends ResponseEntityExceptionHandler {  
  
    @Override  
    protected ResponseEntity<Object> handleMethodArgumentNotValid(  
            MethodArgumentNotValidException ex, HttpHeaders headers, HttpStatusCode status, WebRequest request) {  
        Map<String, String> validationErrors = new HashMap<>();  
        List<ObjectError> validationErrorList = ex.getBindingResult().getAllErrors();  
  
        validationErrorList.forEach((error) -> {  
            String fieldName = ((FieldError) error).getField();  
            String validationMsg = error.getDefaultMessage();  
            validationErrors.put(fieldName, validationMsg);  
        });  
        return new ResponseEntity<>(validationErrors, HttpStatus.BAD_REQUEST);  
    }
}
```