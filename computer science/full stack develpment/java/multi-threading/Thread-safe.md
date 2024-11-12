In [[java]], **thread safety** means that a class or method is safe to be used by multiple threads concurrently without causing inconsistent results or unexpected behavior.

When a class or method is **thread-safe**, it ensures that the data it works with remains in a consistent state even when accessed or modified by multiple threads simultaneously.

# [[Non-Thread-safe]]

from the above non-thread safe, we gonna make this [[Thread-safe]].

To make the class thread-safe, we can use the `synchronized` keyword to ensure that only one thread can increment the counter at a time:

```java
class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;  // Thread-safe increment
    }

    public synchronized int getCount() {
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

        System.out.println(counter.getCount());  // Output will reliably be 2000
    }
}
```

Here, by adding `synchronized` to the `increment()` and `getCount()` methods, only one thread can access these methods at a time, making the class **[[Thread-safe]]**.


# Other approch 
1. [[AtomicInteger]] variable.
2. [[java concurrent]] package: Classes like `ConcurrentHashMap`, `CopyOnWriteArrayList`, and `ReentrantLock` provide thread-safe implementations of common data structures and utilities.