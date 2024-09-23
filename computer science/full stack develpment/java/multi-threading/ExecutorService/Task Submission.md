Submit tasks using methods like `submit()`, `execute()`, and `invokeAll()`.

### **Submitting Tasks**

You can submit tasks to the [[ExecutorService]] using two primary methods:

- **[[execute()]]**: Executes [[Runnable]] tasks but does not return any result.
- **[[submit()]]**: Submits either a [[Runnable]] or a [[Callable]] and returns a [[Future]].

##### **Using `submit()` for `Runnable` (No Result Expected)**:

```java
executorService.submit(() -> {
    System.out.println("Executing Runnable Task");
});
```

##### **Using `submit()` for `Callable` (Result Expected)**:

A `Callable` returns a result, unlike a `Runnable`, which does not return anything.

```java
import java.util.concurrent.*;

public class CallableExample {

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        ExecutorService executor = Executors.newFixedThreadPool(3);

        Callable<String> task = () -> {
            Thread.sleep(2000);  // Simulate long-running task
            return "Task Completed!";
        };

        Future<String> future = executor.submit(task);

        // Block until the result is available
        System.out.println("Result: " + future.get());

        executor.shutdown();
    }
}
```


