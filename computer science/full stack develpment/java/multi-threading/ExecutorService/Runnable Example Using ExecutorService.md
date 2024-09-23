```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class RunnableWithExecutorExample {
    public static void main(String[] args) {
        // Create an ExecutorService with a fixed thread pool
        ExecutorService executorService = Executors.newFixedThreadPool(2);

        // Define a Runnable task
        Runnable task = () -> {
            for (int i = 1; i <= 3; i++) {
                System.out.println("Runnable task: " + i + " in thread " + Thread.currentThread().getName());
                try {
                    Thread.sleep(500);  // Simulate some work
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        };

        // Submit the task to the ExecutorService
        executorService.execute(task);

        // Shutdown the executor
        executorService.shutdown();
    }
}
```

Output: 
```
Runnable task: 1 in thread pool-1-thread-1
Runnable task: 2 in thread pool-1-thread-1
Runnable task: 3 in thread pool-1-thread-1
```

