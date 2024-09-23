[[Runnable]] is a [[functional interface]] (introduced in Java 1.0) that represents a task or work that can be run by a [[thread]]. It is simple, does not return any result, and cannot throw checked exceptions

Key Features of [[Runnable]]
- It does **not** return a result.
- It cannot throw checked exceptions.
- It contains a single method `run()`, which is meant to define the task that will be executed by a thread.
```java
public class RunnableExample {
    public static void main(String[] args) {
        // Create a Runnable task using a lambda expression
        Runnable task = () -> {
            for (int i = 1; i <= 5; i++) {
                System.out.println("Runnable task: " + i);
                try {
                    Thread.sleep(500);  // Simulating some delay
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        };

        // Run the task using a Thread
        Thread thread = new Thread(task);
        thread.start();
    }
}
```

Output:
```
Runnable task: 1
Runnable task: 2
Runnable task: 3
Runnable task: 4
Runnable task: 5
```

#### Key Points:

- `Runnable` tasks are usually executed by a thread (`new Thread(runnable).start()`).
- It is simple to use but lacks the ability to return a result.

# [[Runnable Example Using ExecutorService]]
