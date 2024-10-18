 [[Future]] is a placeholder for a result that is produced by an [[asynchronous]] computation.
 
Tasks submitted via [[submit()]] return a [[Future]] object. You can:

- **Check if the task is done**: `future.isDone()`
- **Block and wait for the result**: `future.get()`
- `get(long timeout, TimeUnit unit)`Retrieves the result of the computation but only waits for the specified timeout. If the result is not available within the time, it throws a `TimeoutException`
- **Cancel the task**: `future.cancel(true)`
- `isCancelled()`

```java
Future<Integer> future = executorService.submit(() -> {
    return 42; // Simulate a computation
});

System.out.println("Task result: " + future.get());
```
