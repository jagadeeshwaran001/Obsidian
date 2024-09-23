[[Dependency injection]] is a programming technique which a [[function]] or a [[computer science/full stack develpment/java/OOPS/Object|Object]] receives the Object of the other class [[computer science/full stack develpment/java/OOPS/Object|Object]] or a [[function]], instead of creating them internally.

ref: code [[Without Dependency Injection]]

code with DI: 

Now, let's decouple the `Car` and `Engine` using **manual dependency injection**, allowing the engine to be passed to the car, making it flexible.

```java
public class Engine {
    public String start() {
        return "Engine started";
    }
}
```

```java
public class ElectricEngine extends Engine {
    @Override
    public String start() {
        return "Electric engine started silently";
    }
}
```

```java
public class Car {
    private Engine engine;

    // Constructor Injection (Engine passed via constructor)
    public Car(Engine engine) {
        this.engine = engine;
    }

    public void drive() {
        System.out.println(engine.start());
        System.out.println("Car is driving...");
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        // Manual Dependency Injection
        Engine engine = new ElectricEngine(); // Injecting ElectricEngine
        Car car = new Car(engine);            // Passing Engine to Car
        car.drive();
    }
}
```

In this example:

- The `Car` no longer creates an instance of `Engine`. Instead, an engine is passed via the constructor.
- The `Main` class decides which engine to use (`ElectricEngine` or `Engine`).
- If you want to switch from a regular engine to an electric engine, you only modify the injection logic in `Main.java`, not the `Car` class.

### Key Benefits of DI:

1. **Loose Coupling**: The `Car` no longer depends on a specific `Engine` implementation.
2. **Flexibility**: You can swap different types of engines (`Engine`, `ElectricEngine`, etc.) without modifying the `Car` class.
3. **Testability**: It's easy to pass mock engines during testing.
