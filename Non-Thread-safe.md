consider the following [[Non-Thread-safe]] example:

```java
class Counter {
    private int count = 0;

    public void increment() {
        count++;  // This is not thread-safe
    }

    public int getCount() {
        return count;
    }
}

public class Main {
    public static void main(String[] args) throws InterruptedException {
        Counter counter = new Counter();

        Runnable task = () -> {
            for (int i = 0; i < 1000; i++) {
                counter.increment();
            }
        };

        Thread thread1 = new Thread(task);
        Thread thread2 = new Thread(task);

        thread1.start();
        thread2.start();

        thread1.join();
        thread2.join();

        System.out.println(counter.getCount());  // Output may not be 2000 due to race conditions
    }
}
```

In this example, two threads (`thread1` and `thread2`) are incrementing the counter concurrently. Since the `increment()` method is not thread-safe, both threads may interfere with each other, leading to inconsistent results (e.g., the output might be less than `2000`).

