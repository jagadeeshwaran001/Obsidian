### **Common Problems Addressed by the Prototype Pattern:**

1. **Costly Object Creation**:
    - If the creation of objects is resource-intensive (e.g., involves database operations, network requests, or heavy computations), creating new instances of these [[computer science/full stack develpment/java/OOPS/Object|Object]] frequently can degrade performance.
2. [[Avoiding Subclass Explosion]]:
    - When a system has many subclasses, each with slightly different initialization logic, managing the creation of these subclasses can be complex and result in a large number of subclasses. Prototypes can reduce the need for excessive subclassing.
3. [[Dynamic Object Creation]]:
    - In cases where the object structure is not known at compile time and must be determined dynamically, the Prototype Pattern allows for the cloning of objects without knowing their concrete classes.

### **Prototype Pattern Solution:**

The Prototype Pattern solves this problem by creating new objects by copying or "cloning" an existing object, which serves as a prototype. The key benefit is that copying an object (shallow or deep copy) is often much cheaper than instantiating it.

### **Prototype Pattern Key Concepts:**

- **Prototype Interface**: Declares a `clone()` method to create a copy of the object.
- **Concrete Prototype Class**: Implements the `clone()` method to return a copy of itself.
- **Client**: Uses the prototype to create new objects by calling the `clone()` method instead of instantiating them.

#### **Example Scenario:**

Imagine you are designing a system where you need to create various types of cars. Creating each car involves expensive operations (e.g., accessing a database to load car details). To avoid the cost of recreating similar cars multiple times, you can create a prototype car, and then clone it when you need a new instance.

### **Prototype Pattern Example:**

#### **Step 1: Define the Prototype Interface (`Cloneable`)**
```java
public interface PrototypeCar extends Cloneable {
    // Prototype method to clone an object
    Car clone() throws CloneNotSupportedException;
}
```
Step 2: Implement the Concrete Prototype (`Car`)
```java
public class Car implements PrototypeCar {
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

    // Overriding clone method to create a new copy of Car object
    @Override
    public Car clone() throws CloneNotSupportedException {
        return (Car) super.clone();
    }

    @Override
    public String toString() {
        return "Car [Model=" + model + ", Engine=" + engine + ", Color=" + color + "]";
    }
}
```

Step 3: Client Code Using the Prototype
```java
public class PrototypePatternDemo {
    public static void main(String[] args) {
        try {
            // Original Car (Prototype)
            Car originalCar = new Car("Sedan", "V8", "Red");
            System.out.println("Original Car: " + originalCar);

            // Clone the original car
            Car clonedCar1 = originalCar.clone();
            System.out.println("Cloned Car 1: " + clonedCar1);

            // Modify the cloned car
            Car clonedCar2 = clonedCar1.clone();
            System.out.println("Cloned Car 2: " + clonedCar2);
        } catch (CloneNotSupportedException e) {
            e.printStackTrace();
        }
    }
}
```
### **Explanation:**

- **Prototype Interface (`PrototypeCar`)**: Declares the `clone()` method, which will be used to clone objects.
- **Concrete Prototype (`Car`)**: Implements the `clone()` method, enabling the creation of new instances by copying the existing object.
- **Client**: Uses the prototype to clone new cars without creating them from scratch, saving time and resources.
#### output:
```
Original Car: Car [Model=Sedan, Engine=V8, Color=Red]
Cloned Car 1: Car [Model=Sedan, Engine=V8, Color=Red]
Cloned Car 2: Car [Model=Sedan, Engine=V8, Color=Red]
```


# [[without prototype pattern]]

# DeepCopy of object

```java
@Override
public Object clone() throws CloneNotSupportedException {
    Car clonedCar = (Car) super.clone();
    clonedCar.engine = new Engine(this.engine.getType());  // Deep copy of mutable field
    return clonedCar;
}
```

### Interview Quesitons:

### **Can the Prototype Pattern be used with immutable objects?**

**Answer:** No, the Prototype Pattern is generally not suitable for immutable objects because immutability implies that the state of the object cannot change after it has been created. Cloning and modifying cloned objects conflict with the concept of immutability.