Creates new [[thread]]s as needed and reuses previously created threads when available. Idle threads are terminated if not used for 60 seconds.

```java
ExecutorService executor = Executors.newCachedThreadPool();
```

**Best for**: Applications with unpredictable task loads (e.g., server handling many simultaneous requests).
