[[Callable]] is another [[functional interface]] (introduced in Java 5 with [[java.util]].concurrent), similar to [[Runnable]], but it is designed to return a result and can throw checked exceptions.

#### Key Features of `Callable`:

- It **returns a result**.
- It can **throw checked exceptions**.
- It contains a single method `call()`, which defines the task and returns a result.
### **Example of `Callable`**

In this example, we will create a `Callable` task that computes the sum of numbers from 1 to 5 and returns the result.

```java
import java.util.concurrent.*;

public class CallableExample {
    public static void main(String[] args) {
        // Create a Callable task to compute a sum
        Callable<Integer> task = () -> {
            int sum = 0;
            for (int i = 1; i <= 5; i++) {
                sum += i;
                Thread.sleep(500);  // Simulating delay
            }
            return sum;  // Return the result
        };

        // Use ExecutorService to execute the task and get the result
        ExecutorService executor = Executors.newFixedThreadPool(1);
        Future<Integer> future = executor.submit(task);

        try {
            // Get the result from the Callable task (blocks until the task completes)
            Integer result = future.get();
            System.out.println("Sum of numbers: " + result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        } finally {
            executor.shutdown();
        }
    }
}
```

##### output: 
```
Sum of numbers: 15
```

#### Key Points:

- The `Callable` task can be submitted to an `ExecutorService` using `submit()`, which returns a `Future`.
- The result of the task can be retrieved using `future.get()`, which blocks until the computation is done.
# [[Callable Example Using ExecutorService]]