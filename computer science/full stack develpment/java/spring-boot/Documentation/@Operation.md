This [[swagger-annotation]] is used to mention the summary and description of the specific [[REST Endpoint]] to document as per the [[Swagger open-api]].

This annotation can only be used in the method level.

```java
@Operation(
            summary = "Fetch Account Details REST API",
            description = "REST API to fetch Customer &  Account details based on a mobile number"
    )
    @GetMapping("/fetch")
    public ResponseEntity<CustomerDto> fetchAccountDetails(@RequestParam
                                                               @Pattern(regexp="(^$|[0-9]{10})",message = "Mobile number must be 10 digits")
                                                               String mobileNumber) {
        CustomerDto customerDto = iAccountsService.fetchAccount(mobileNumber);
        return ResponseEntity.status(HttpStatus.OK).body(customerDto);
    }
```

