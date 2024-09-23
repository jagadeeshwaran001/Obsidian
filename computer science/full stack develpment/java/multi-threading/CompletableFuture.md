You can also use `CompletableFuture` to run tasks asynchronously and chain further actions after the completion of the task.

This is also present in [[java utils]].concurrent

You can also use `CompletableFuture` to run tasks asynchronously and chain further actions after the completion of the task.

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureDemo {
    public static void main(String[] args) {
        CompletableFuture<Void> future = CompletableFuture.runAsync(() -> {
            // Simulating a long-running task
            try {
                System.out.println("Running task in: " + Thread.currentThread().getName());
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("Task Completed!");
        });

        // Block and wait for the future to complete (for demonstration purposes)
        future.join();
    }
}
```

In this example:

- `runAsync()` runs the code asynchronously in a separate thread, and `join()` blocks until the task completes.
- The output would show that the task is running in a separate thread, then prints "Task Completed!" after 2 seconds.

> ===You can combine `CompletableFuture` with `@Async` and handle the result in your controllers.===

---

### **Using `CompletableFuture`**

#### Pros:

- **Asynchronous and Non-blocking**: `CompletableFuture` allows non-blocking code execution, and it can be easily composed to execute a chain of tasks asynchronously.
- **Combining Multiple Async Tasks**: It’s great for scenarios where you need to combine or chain multiple asynchronous operations (e.g., handle a result after multiple async tasks finish).
- **Functional and Declarative**: Provides a more functional programming approach to asynchronous tasks. It allows for composing, joining, and handling exceptions in an elegant way.
- **Better Control over Return Types**: Unlike `@Async`, `CompletableFuture` lets you easily return values from asynchronous tasks, making it useful when the result of an async operation is needed in further computation.

#### Cons:

- **Complexity in Chaining**: [[Chaining multiple asynchronous tasks]] can become complex and harder to debug if not handled properly.
- **Thread Management**: Although it is more flexible than `@Async`, you still need to manage the underlying `ExecutorService` to prevent resource exhaustion.
- **Overhead**: For simple tasks, using `CompletableFuture` might be overkill due to its additional features.

#### Best Use Case:

- When you need to run multiple asynchronous tasks and combine their results, or when you need to chain tasks that depend on each other. It’s also great when you want non-blocking code execution with easy handling of async results.