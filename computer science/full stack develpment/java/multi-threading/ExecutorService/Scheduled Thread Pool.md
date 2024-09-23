Allows tasks to be scheduled to run at a certain time or to execute periodically.

```java
ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(2);
```

**Best for**: Scheduling periodic tasks (like sending reminders or monitoring server health).
