Using an appropriate type of [[ExecutorService]] based on the workload helps with performance optimization:
- For tasks with varying durations, use [[newCachedThreadPool()]] to avoid idle threads.
- For a fixed number of tasks, [[newFixedThreadPool()]] ensures a predictable level of concurrency.