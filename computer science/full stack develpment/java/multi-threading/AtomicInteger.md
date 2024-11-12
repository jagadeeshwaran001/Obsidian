**Using Atomic Variables:** The `AtomicInteger` class provides a thread-safe way to perform atomic operations on integers without using `synchronized`.

```java
import java.util.concurrent.atomic.AtomicInteger;

class Counter {
    private AtomicInteger count = new AtomicInteger(0);

    public void increment() {
        count.getAndIncrement();
    }

    public int getCount() {
        return count.get();
    }
}
```
