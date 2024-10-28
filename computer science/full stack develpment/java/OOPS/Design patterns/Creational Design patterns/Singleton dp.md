[[Singleton dp]] ensure that a class has only one instance throughout the application and providing the global point of access to that instance.

In a software system, there is a need to control access to a shared resource (such as a database connection, configuration manager, or logging system). Creating multiple instances of the resource could lead to inconsistent behavior, unnecessary resource consumption, or conflicts. Additionally, having multiple points of access to the same shared resource can lead to [[synchronization]] issues in a [[computer science/Software Engineering/multi-threading]] environment.

To solve this, we need a mechanism that:

1. Ensures only **one instance** of the class is created, regardless of how many times the class is requested.
2. Provides a **global point of access** to the instance, so any part of the system can access the shared resource.
3. Lazily creates the instance (if necessary), meaning the instance is only created when it is first requested.

Two types of [[Singleton dp]].

**1.Basic [[Singleton dp]]:**

```java
public class Singleton {
    // Step 1: Private static variable to hold the single instance of the class
    private static Singleton instance;

    // Step 2: Private constructor to prevent instantiation from outside the class
    private Singleton() {
        // Prevent instantiation
    }

    // Step 3: Public static method to provide the single instance of the class
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton(); // Create the instance lazily (only when requested)
        }
        return instance; // Return the single instance
    }
}
```

---

**2.[[Thread-safe]] [[Singleton dp]]:**

In [[computer science/Software Engineering/multi-threading]] environment one or more thread can call `getInstance()` method at a time. Leading to multiple instance can being created. To avoid this, you can make the [[Singleton dp]] [[Thread-safe]].

[[synchronized]] [[Keyword]] used to ensure [[Thread-safe]].

```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {}

    // Synchronized method to ensure thread-safety
    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

The `getInstance()` method is synchronized, ensuring that only one thread can access it at a time. This prevents multiple threads from creating more than one instance simultaneously.

**Downside**: Synchronizing the entire method can be costly in terms of performance, especially when the method is called frequently. After the first instance is created, the synchronization overhead is unnecessary, so the below method can be helpful.

---

**3.Double-Checked Locking**

Double-Checked Locking is a performance improvement over the synchronized method. It reduces the overhead of acquiring the lock after the instance has been initialized.

```java
public class Singleton {
    private static volatile Singleton instance;  // Volatile to ensure visibility of changes across threads

    private Singleton() {}

    public static Singleton getInstance() {
        if (instance == null) {
            synchronized (Singleton.class) {  // Only synchronize if the instance is null
                if (instance == null) {
                    instance = new Singleton();  // Create the instance
                }
            }
        }
        return instance;
    }
}
```

- **Double-checking**: The first `if (instance == null)` check ensures that we only synchronize the block if the instance hasn’t been created yet. Once an instance is created, subsequent calls to `getInstance()` skip the synchronized block.
- **Synchronized block**: Inside the synchronized block, we check `instance == null` again to ensure that no other thread created an instance while the first thread was waiting for the lock.
- **[[Volatile]] [[keyword]]**: The `instance` is declared [[volatile]] to ensure that changes made by one thread to the `instance` are visible to all other threads.
---

4.**Eager Initialization**:

If your Singleton class is lightweight and you are certain it will always be used, you can create the instance eagerly when the class is loaded, rather than waiting for it to be requested.

```java
public class Singleton {
    // Eagerly creating the instance when the class is loaded
    private static final Singleton instance = new Singleton();

    private Singleton() {}

    public static Singleton getInstance() {
        return instance;  // Return the pre-created instance
    }
}
```

**Explanation**:
- **Eager Initialization**: The instance is created as soon as the class is loaded into memory, without waiting for the `getInstance()` method to be called.
- **Advantage**: This avoids synchronization issues since the instance is created at class loading time.
- **Disadvantage**: If the Singleton instance is never used, the memory allocated for it is wasted.
---

5.**Bill Pugh Singleton (Lazy Initialization Holder Class)**

This is considered the best way to implement a Singleton in Java because it is both thread-safe and efficient.

```java
public class Singleton {

    private Singleton() {}

    // Inner static class responsible for holding the Singleton instance
    private static class SingletonHelper {
        private static final Singleton INSTANCE = new Singleton();
    }

    // Public method to provide access to the Singleton instance
    public static Singleton getInstance() {
        return SingletonHelper.INSTANCE;
    }
}
```

**Explanation**:

- **Lazy Initialization**: The `SingletonHelper` class is not loaded until `getInstance()` is called. This ensures that the Singleton instance is created only when it is needed.
- **Thread-Safe**: The Java class loader guarantees that this initialization happens in a thread-safe manner.
- **Efficient**: No synchronization is required, making it more efficient than synchronized methods or double-checked locking.
---

5.**Enum Singleton (Best Practice)**:

Java’s `enum` is a convenient and simple way to implement the Singleton pattern. It is thread-safe, guarantees a single instance, and also protects against serialization attacks.

```java
public enum Singleton {
    INSTANCE;

    public void someMethod() {
        // Your business logic here
    }
}
```

**Explanation**:

- **Enum**: The Java `enum` type inherently provides [[Thread-safe]]ty and guarantees that only one instance of the enum exists within the JVM.
- **Serialization-safe**: Java ensures that the [[enum]] singleton is safe from [[serialization]] and [[deserialization]] attacks, which can otherwise break single-instance guarantees.

**Drawbacks**: no Lazy Initialization.

---
### 6. **Comparison of Singleton Implementations**

| Implementation          | Thread Safety | Lazy Initialization | Complexity | Performance Impact                       |
| ----------------------- | ------------- | ------------------- | ---------- | ---------------------------------------- |
| Basic (Non-thread-safe) | No            | Yes                 | Low        | High (due to potential race conditions)  |
| Synchronized Method     | Yes           | Yes                 | Low        | Medium (due to synchronization overhead) |
| Double-Checked Locking  | Yes           | Yes                 | Medium     | Low (better performance)                 |
| Eager Initialization    | Yes           | No                  | Low        | None (instantiated at startup)           |
| Bill Pugh Singleton     | Yes           | Yes                 | Medium     | None (best performance)                  |
| Enum Singleton          | Yes           | No                  | Very Low   | None                                     |

---



