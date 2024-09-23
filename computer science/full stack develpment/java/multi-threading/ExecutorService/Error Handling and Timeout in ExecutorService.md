You can handle errors by catching exceptions from `Future.get()`, and you can also set a timeout.

#### Example: Handling Timeout with `Future.get()`:

```java
try {
    String result = future.get(1, TimeUnit.SECONDS);  // Wait for max 1 second
} catch (TimeoutException e) {
    System.out.println("Task timed out!");
} catch (ExecutionException | InterruptedException e) {
    e.printStackTrace();
}
```

