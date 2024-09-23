One of the key features is the [[CompletableFuture]] is chaining multiple [[asynchronous]] operations.

we can execute ==sequentially== or ==parallel== and then ==combain== their results.


# **Chaining CompletableFutures:**
#### Example: Chaining Tasks Sequentially with `thenApply`, `thenAccept`, and `thenRun`

- **`thenApply()`**: Transforms the result of one computation and passes it to the next stage.
- **`thenAccept()`**: Consumes the result of the previous stage but doesn’t return anything.
- **`thenRun()`**: Runs after a computation completes but doesn't receive its result.

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureChainingExample {

    public static void main(String[] args) {
        CompletableFuture<Void> future = CompletableFuture.supplyAsync(() -> {
            System.out.println("Step 1: Fetching user details...");
            // Simulate a delay
            sleep(1000);
            return "User: John";
        }).thenApply(user -> {
            System.out.println("Step 2: Fetching order for " + user);
            // Simulate a delay
            sleep(1000);
            return "Order: Laptop";
        }).thenAccept(order -> {
            System.out.println("Step 3: Sending notification for " + order);
            // Simulate sending a notification
            sleep(1000);
        }).thenRun(() -> {
            System.out.println("Step 4: Task Completed, cleaning up...");
        });

        // Block until the entire chain is completed (for demo purposes)
        future.join();
    }

    private static void sleep(int ms) {
        try {
            Thread.sleep(ms);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

**output:**

```
Step 1: Fetching user details...
Step 2: Fetching order for User: John
Step 3: Sending notification for Order: Laptop
Step 4: Task Completed, cleaning up...
```

# Handling Multiple Async Operations in Parallel

You can run multiple `CompletableFuture`s in parallel and combine their results using methods like:

- **`thenCombine()`**: Combines results from two independent futures.
- **`allOf()`**: Waits for all futures to complete.
- **`anyOf()`**: Completes when any of the futures completes.

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureCombineExample {

    public static void main(String[] args) {
        CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> {
            sleep(1000);
            return "Result from Future 1";
        });

        CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> {
            sleep(2000);
            return "Result from Future 2";
        });

        CompletableFuture<String> combinedFuture = future1.thenCombine(future2, (result1, result2) -> {
            return result1 + " & " + result2;
        });

        System.out.println("Combined Result: " + combinedFuture.join());
    }

    private static void sleep(int ms) {
        try {
            Thread.sleep(ms);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

##### output:
```
Combined Result: Result from Future 1 & Result from Future 2
```

**Explanation**:

- Two tasks run in parallel (`future1` and `future2`).
- Once both tasks are complete, `thenCombine()` merges the results from both tasks.
- The final result is printed as `"Result from Future 1 & Result from Future 2"`.

# Exception Handling in CompletableFutures

You can handle exceptions that occur in any stage of the `CompletableFuture` chain using methods like:

- **`exceptionally()`**: Handles exceptions and returns a default value.
- **`handle()`**: Handles both the result and the exception.

#### Example: Using `exceptionally` to Handle Errors

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureExceptionHandlingExample {

    public static void main(String[] args) {
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            System.out.println("Executing task...");
            if (true) { // Simulating an error
                throw new RuntimeException("Something went wrong!");
            }
            return "Success!";
        }).exceptionally(ex -> {
            System.out.println("Handling exception: " + ex.getMessage());
            return "Fallback result";
        });

        System.out.println("Final Result: " + future.join());
    }
}
```

##### output
```
Executing task...
Handling exception: Something went wrong!
Final Result: Fallback result
```

**Explanation**:

- The task throws an exception (`RuntimeException`).
- The `exceptionally()` block catches the exception and provides a fallback result (`"Fallback result"`).
- The final result will print the fallback value due to the exception.

# Waiting for All Tasks to Complete using ===`allOf()`===

If you need to wait for a group of tasks to complete, you can use `CompletableFuture.allOf()`.

#### Example: Using `allOf` to Wait for Multiple Tasks

```java
import java.util.concurrent.CompletableFuture;
import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CompletableFutureAllOfExample {

    public static void main(String[] args) {
        CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> {
            sleep(1000);
            return "Task 1 Result";
        });

        CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> {
            sleep(2000);
            return "Task 2 Result";
        });

        CompletableFuture<String> future3 = CompletableFuture.supplyAsync(() -> {
            sleep(1500);
            return "Task 3 Result";
        });

        // Wait for all tasks to complete
        CompletableFuture<Void> allFutures = CompletableFuture.allOf(future1, future2, future3);

        // When all futures are done, collect the results
        CompletableFuture<List<String>> allResults = allFutures.thenApply(v -> 
            Stream.of(future1, future2, future3)
                .map(CompletableFuture::join)
                .collect(Collectors.toList())
        );

        System.out.println("All Results: " + allResults.join());
    }

    private static void sleep(int ms) {
        try {
            Thread.sleep(ms);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

##### output
```
All Results: [Task 1 Result, Task 2 Result, Task 3 Result]
```

Explanation: 

- `allOf()` waits for all tasks (`future1`, `future2`, and `future3`) to complete.
- After all tasks finish, their results are collected using `Stream.of(...).map(CompletableFuture::join)`.

### Conclusion:

`CompletableFuture` is a flexible way to handle asynchronous programming, allowing for chaining, combining, and handling multiple tasks in parallel. It offers robust error handling, non-blocking execution, and supports combining results from multiple asynchronous operations, making it ideal for complex, real-world applications requiring efficient concurrency management.

