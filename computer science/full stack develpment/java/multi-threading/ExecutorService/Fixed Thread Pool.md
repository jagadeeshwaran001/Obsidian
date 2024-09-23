A fixed number of [[thread]]s are created and reused to execute tasks. If the pool is full, new tasks are queued until a thread is free.

```java
ExecutorService executor = Executors.newFixedThreadPool(3);  // 3 threads
```

**Best for**: Applications with a steady number of tasks, like database processing or a fixed number of clients.