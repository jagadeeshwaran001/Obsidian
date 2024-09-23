In situations where the exact type of object to be created is determined at runtime, the Prototype Pattern allows you to create objects dynamically by cloning existing prototypes. This is useful when you have a complex system and need to create objects based on user input or other dynamic factors.

#### **Example of Dynamic Object Creation**

Imagine an application where a user can choose to create a new car dynamically, based on a prototype. Instead of writing a specific constructor for each type of car, you clone a prototype based on the user’s preferences.

```java
import java.util.HashMap;
import java.util.Map;

// Car Prototype Factory
class CarPrototypeFactory {
    private static Map<String, Car> prototypes = new HashMap<>();

    static {
        prototypes.put("Sedan", new Car("V6", "Red"));
        prototypes.put("SUV", new Car("V8", "Black"));
    }

    // Method to clone a prototype based on the user's choice
    public static Car getCar(String type) {
        return prototypes.get(type).clone();
    }
}

public class DynamicObjectCreation {
    public static void main(String[] args) {
        // User dynamically chooses to create an SUV
        Car userChosenCar = CarPrototypeFactory.getCar("SUV");
        userChosenCar.setColor("Blue");  // Modify the cloned car as needed
        userChosenCar.displayDetails();  // Output: Car with engine: V8, color: Blue

        // User chooses to create another Sedan
        Car anotherCar = CarPrototypeFactory.getCar("Sedan");
        anotherCar.displayDetails();     // Output: Car with engine: V6, color: Red
    }
}
```

#### **Explanation:**

- **Prototype Factory**: `CarPrototypeFactory` holds a collection of prototype objects (`Sedan` and `SUV`).
- **Dynamic Creation**: The user’s choice determines which car prototype is cloned and created at runtime, allowing for dynamic object creation.
- **Modifying Prototypes**: After cloning the prototype, you can modify it to suit the user's preferences (e.g., changing the car’s color).

### **Advantages of Dynamic Object Creation with Prototype:**

1. **Runtime Flexibility**: New objects can be created at runtime based on dynamic input without needing a complex hierarchy of subclasses.
2. **Customization**: After cloning the prototype, the object can be customized (e.g., change color or engine) without altering the original prototype.
3. **Decoupling Object Creation**: The client code doesn't need to know the specifics of how objects are created. It just clones the prototype, which decouples object creation from the client.