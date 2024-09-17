Defines an interface for creating objects, but lets subclasses alter the type of objects that will be created.

**Problem statement:**

In a software system, we may have a requirement to crate a [[computer science/full stack develpment/OOPS/Object|Object]] that belongs to the family of related class. That specific object should be determined only in the run time based on some inputs or a configurations. Directly instantiate can lead the code to [[Tightly-coupled]] to specific class.

- **Decouple Code**: Avoid tight coupling between client code and the concrete classes it needs to instantiate.
- **Extend Functionality**: Introduce new classes or change the instantiation process without modifying the existing code.
- **Manage Object Creation**: Control and manage the instantiation process in a way that promotes flexibility and maintainability.

To address these issues, the Factory Method pattern provides an interface for creating objects but lets subclasses alter the type of objects that will be created.

**Solution:**

The Factory Method pattern proposes the following solution:

1. **Define a Common Interface**: Create an [[abstract class]] or [[interface]] that declares the factory method which will return the [[computer science/full stack develpment/OOPS/Object|Object]].
2. **Concrete Implementations**: Subclasses or concrete implementations will override the factory method to return an instance of a specific class.
3. **Client Code**: The client code interacts with the factory method through the common [[interface]] or [[abstract class]], not directly with the [[concrete class]]es.

**code example**:

Step 1: Define the Car Interface

```java
public interface Car {
    void drive();
}
```

Step 2: Implement Concrete Car Classes

```java
public class Sedan implements Car {
    @Override
    public void drive() {
        System.out.println("Driving a Sedan.");
    }
}
```

```java
public class SUV implements Car {
    @Override
    public void drive() {
        System.out.println("Driving an SUV.");
    }
}
```

Step 3: Define the CarFactory Interface

```java
public interface CarFactory {
    Car createCar();
}
```

Step 4: Implement Concrete Car Factories

```java
public class SedanFactory implements CarFactory {
    @Override
    public Car createCar() {
        return new Sedan();
    }
}
```

```java
public class SUVFactory implements CarFactory {
    @Override
    public Car createCar() {
        return new SUV();
    }
}
```

Step 5: Implement the Client Code

```java
public class CarClient {
    private CarFactory carFactory;

    public CarClient(CarFactory carFactory) {
        this.carFactory = carFactory;
    }

    public void driveCar() {
        Car car = carFactory.createCar();
        car.drive();
    }

    public static void main(String[] args) {
        // Client code using SedanFactory
        CarFactory sedanFactory = new SedanFactory();
        CarClient sedanClient = new CarClient(sedanFactory);
        sedanClient.driveCar();

        // Client code using SUVFactory
        CarFactory suvFactory = new SUVFactory();
        CarClient suvClient = new CarClient(suvFactory);
        suvClient.driveCar();
    }
}
```
### **Explanation:**

1. **Car Interface**:
    
    - Defines the common interface for all car types with the `drive` method.
2. **Concrete Car Classes**:
    
    - `Sedan` and `SUV` implement the `Car` interface and provide specific implementations of the `drive` method.
3. **CarFactory Interface**:
    
    - Declares the factory method `createCar` which will return a `Car` instance.
4. **Concrete Car Factories**:
    
    - `SedanFactory` and `SUVFactory` implement the `CarFactory` interface and override the `createCar` method to instantiate and return the appropriate `Car` type.
5. **Client Code**:
    
    - `CarClient` uses a `CarFactory` to create `Car` instances. The client does not need to know the specific type of car being created. It simply calls `createCar` on the factory and uses the resulting `Car` object.


>If suppose we need to introduce the new Car type as `HatchBack` we doesn't need to change the existing code classes.
>

>We can add the `HatchBack` class which implements `Car` and add `HatchBackFactory` class which implements `CarFactory`.

>Now only the client class code is enough to create a object for `HatchBack` car.


for better understating refer [[Without Factory Method dp]] 