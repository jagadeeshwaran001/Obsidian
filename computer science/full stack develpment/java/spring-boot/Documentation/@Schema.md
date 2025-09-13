This [[swagger-annotation]] can be used as both class level and method level for [[Swagger open-api]] docs.

This is used to document the Request and Response type of the [[REST Endpoint]].

The `example` attribute is used to mention the default or example input or output for the specific field in the documentation.

eg:

```java
@Schema(
        name = "Accounts",
        description = "Schema to hold Account information"
)
public class AccountsDto {

    @NotEmpty(message = "AccountNumber can not be a null or empty")
    @Pattern(regexp="(^$|[0-9]{10})",message = "AccountNumber must be 10 digits")
    @Schema(
            description = "Account Number of Eazy Bank account", example = "3454433243"
    )
    private Long accountNumber;

    @NotEmpty(message = "AccountType can not be a null or empty")
    @Schema(
            description = "Account type of Eazy Bank account", example = "Savings"
    )
    private String accountType;

    @NotEmpty(message = "BranchAddress can not be a null or empty")
    @Schema(
            description = "Eazy Bank branch address", example = "123 NewYork"
    )
    private String branchAddress;
}
```

>By Default the [[Swagger open-api]] does not scan the [[Global Exception]] class. So The response of the error will not ne caught in [[Swagger open-api]]. To rectify this we need to mention a [[spring-annotation]] `@Content` with `@Schema` in [[@ApiResponses or @ApiResponses]].

eg:

```java

@ApiResponse(
		responseCode = "500",
		description = "HTTP Status Internal Server Error",
		content = @Content(
				schema = @Schema(implementation = ErrorResponseDto.class)
		)
)
@PostMapping("/create")
public ResponseEntity<ResponseDto> createAccount(@Valid @RequestBody CustomerDto customerDto) {
	iAccountsService.createAccount(customerDto);
	return ResponseEntity
			.status(HttpStatus.CREATED)
			.body(new ResponseDto(AccountsConstants.STATUS_201, AccountsConstants.MESSAGE_201));
}
```

