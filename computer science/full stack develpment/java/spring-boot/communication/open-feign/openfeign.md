1. First we need to add the dependency to the project.
2. Then we need to annotate the main application with [[@EnableFeignClients]] annotation.
3. We need to create a [[interface]] and annotate the interface with [[@FeignClient("serviceName")]], service name is nothing but a name we used to mention that in a [[Eureka server]]
4. Then we need to mock the api code form the clinet to this microservice.

>The good this is [[openfeign]] will cache the data for 30 sec by default.

eg:

If we need to call the cards microservice from accounts microservice, then if the below is the endpoint in the cards microservice.

```java
@GetMapping("/fetch")
    public ResponseEntity<CardsDto> fetchCardDetails(@RequestParam
                                                               @Pattern(regexp="(^$|[0-9]{10})",message = "Mobile number must be 10 digits")
                                                               String mobileNumber) {
        CardsDto cardsDto = iCardsService.fetchCard(mobileNumber);
        return ResponseEntity.status(HttpStatus.OK).body(cardsDto);
    }
```

Then in the accounts microservice we need to write a interface with the method similar to this.

```java
@FeignClient("cards")
public interface CardsFeignClient {

    @GetMapping(value = "/api/fetch",consumes = "application/json")
    public ResponseEntity<CardsDto> fetchCardDetails(@RequestParam String mobileNumber);

}
```

> we don't need to mention the validation thing in the method in this interface.