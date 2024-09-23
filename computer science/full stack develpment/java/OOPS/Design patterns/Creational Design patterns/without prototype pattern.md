Without the Prototype Pattern, every time you need a new `Car` object, you would have to create it from scratch, even if it’s similar to other existing objects.

Step 1: Define the Car Class Without Prototype

```java
public class Car {
    private String model;
    private String engine;
    private String color;

    // Constructor
    public Car(String model, String engine, String color) {
        this.model = model;
        this.engine = engine;
        this.color = color;
    }

    // Getters
    public String getModel() {
        return model;
    }

    public String getEngine() {
        return engine;
    }

    public String getColor() {
        return color;
    }

    @Override
    public String toString() {
        return "Car [Model=" + model + ", Engine=" + engine + ", Color=" + color + "]";
    }
}
```

Step 2: Client Code Without Prototype

```java
public class WithoutPrototypeDemo {
    public static void main(String[] args) {
        // Creating a car from scratch
        Car car1 = new Car("Sedan", "V8", "Red");
        System.out.println("Car 1: " + car1);

        // Creating another car from scratch (even if it is similar to car1)
        Car car2 = new Car("Sedan", "V8", "Red");
        System.out.println("Car 2: " + car2);

        // Creating another similar car from scratch
        Car car3 = new Car("Sedan", "V8", "Blue");
        System.out.println("Car 3: " + car3);
    }
}
```

#### output
```
Car 1: Car [Model=Sedan, Engine=V8, Color=Red]
Car 2: Car [Model=Sedan, Engine=V8, Color=Red]
Car 3: Car [Model=Sedan, Engine=V8, Color=Blue]
```

### **Problems with this Approach (Without Prototype Pattern):**

1. **Inefficient Object Creation**: Even though `car1` and `car2` are identical, we have to create them from scratch, which can be resource-intensive, especially for large or complex objects.
    
2. **Code Duplication**: If a lot of `Car` objects with similar properties are required, the constructor is repeatedly called with the same parameters, leading to code duplication.
    
3. **Lack of Flexibility**: In cases where you need to create similar objects dynamically at runtime, this approach doesn’t allow you to modify or clone existing objects easily.