After tasks are submitted, you need to shut down the [[ExecutorService]] to free resources. There are two key methods for this:

- Shutdown Gracefully
	Allows existing tasks to finish but does not accept new tasks.
	
```java
executorService.shutdown();
```
- **Shutdown Immediately**:
	Attempts to stop all actively executing tasks and returns a list of tasks that were waiting to execute.
```java
List<Runnable> notExecutedTasks = executorService.shutdownNow();
```

