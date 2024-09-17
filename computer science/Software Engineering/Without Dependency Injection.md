code example:

```java
public class Engine { 
	public String start() { 
		return "Engine started"; 
	} 
}
```

```java
public class Car {
    private Engine engine;

    public Car() {
        this.engine = new Engine(); // Directly creating Engine inside Car
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
        Car car = new Car(); // Car internally creates Engine
        car.drive();
    }
}
```

In this case, the `Car` directly depends on a specific `Engine` class and creates an instance of it internally. This leads to **tight coupling** between the `Car` and `Engine` classes.

In this example:

- The `Car` class directly creates an instance of `Engine`.
- If you want to replace the `Engine` with another type of engine (e.g., an `ElectricEngine`), you would need to modify the `Car` class.


