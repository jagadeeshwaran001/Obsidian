**Thread Pooling**: Efficiently manages a pool of threads to execute tasks, reusing threads to avoid overhead.

##### example:
The thread pool is a fixed thread size if the number of task is exceeded then code wait for the thread allocation.

```java
package com.rfpio.server.migration.process;

import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class ExecutorServiceExample {

    public static void main(String[] args) {
        // Create an ExecutorService with a fixed thread pool size of 3
        ExecutorService executorService = Executors.newFixedThreadPool(3);

        // Submit tasks to the ExecutorService
        executorService.submit(() -> {
            System.out.println("Task 1 is running in thread: " + Thread.currentThread().getName());
        });

        executorService.submit(() -> {
            System.out.println("Task 2 is running in thread: " + Thread.currentThread().getName());
        });

        executorService.submit(() -> {
            System.out.println("Task 3 is running in thread: " + Thread.currentThread().getName());
        });
        
        executorService.submit(() -> {
            System.out.println("Task 4 is running in thread: " + Thread.currentThread().getName());
        });
        
        executorService.submit(() -> {
            System.out.println("Task 5 is running in thread: " + Thread.currentThread().getName());
        });
        
        executorService.submit(() -> {
            System.out.println("Task 6 is running in thread: " + Thread.currentThread().getName());
        });

        // Shutdown the ExecutorService gracefully
        executorService.shutdown();
    }
}
```

#### output:
```
Task 1 is running in thread: pool-1-thread-1
Task 2 is running in thread: pool-1-thread-2
Task 3 is running in thread: pool-1-thread-3
Task 4 is running in thread: pool-1-thread-3
Task 5 is running in thread: pool-1-thread-1
Task 6 is running in thread: pool-1-thread-2
```
### note: we execute the executor for 6 times, only 3 threads is allocated, other 3 tasks are wait until one of the thread is available.

