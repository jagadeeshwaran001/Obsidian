## Without the [[Builder dp]]:

```java
public class Car {
    private String engine;
    private String model;
    private boolean GPS;
    private boolean sunroof;
    private boolean airbags;

    public Car(String engine, String model, boolean GPS, boolean sunroof, boolean airbags) {
        this.engine = engine;
        this.model = model;
        this.GPS = GPS;
        this.sunroof = sunroof;
        this.airbags = airbags;
    }
}
```

creating object 

```java
Car car = new Car("V8", "Sedan", true, false, true);
```

> It requires all the parameter, first 2 parameter are only the mandatory one, but still we has to pass all the params


## With [[Builder dp]]

#### step 1:
define a `Car` object 

```java
public class Car {
    // Mandatory attributes
    private String engine;
    private String model;

    // Optional attributes
    private boolean GPS;
    private boolean sunroof;
    private boolean airbags;

    // Private constructor to enforce object creation via builder
    private Car(CarBuilder builder) {
        this.engine = builder.engine;
        this.model = builder.model;
        this.GPS = builder.GPS;
        this.sunroof = builder.sunroof;
        this.airbags = builder.airbags;
    }

    @Override
    public String toString() {
        return "Car [Engine=" + engine + ", Model=" + model + 
                ", GPS=" + GPS + ", Sunroof=" + sunroof + ", Airbags=" + airbags + "]";
    }

    // Builder class
    public static class CarBuilder {
        // Mandatory attributes
        private String engine;
        private String model;

        // Optional attributes with default values
        private boolean GPS = false;
        private boolean sunroof = false;
        private boolean airbags = false;

        // Constructor for mandatory attributes
        public CarBuilder(String engine, String model) {
            this.engine = engine;
            this.model = model;
        }

        // Setter methods for optional attributes
        public CarBuilder setGPS(boolean GPS) {
            this.GPS = GPS;
            return this;  // Return the builder instance for chaining
        }

        public CarBuilder setSunroof(boolean sunroof) {
            this.sunroof = sunroof;
            return this;
        }

        public CarBuilder setAirbags(boolean airbags) {
            this.airbags = airbags;
            return this;
        }

        // Build method to return the final Car object
        public Car build() {
            return new Car(this);  // Pass the builder instance to the private constructor
        }
    }
}
```

### **Explanation of the Code:**

1. **Mandatory Attributes**: `engine` and `model` are passed through the builder’s constructor to ensure these fields are always set.
2. **Optional Attributes**: `GPS`, `sunroof`, and `airbags` are optional and are set using "setter-like" methods (`setGPS()`, `setSunroof()`, `setAirbags()`).
3. **Immutable Object**: The `Car` object is immutable since all attributes are set during the building process, and there are no setters in the `Car` class.
4. **Fluent API**: The `CarBuilder` methods return the builder itself, enabling method chaining (a fluent API style).

usage:

```java
public class CarBuilderDemo {
    public static void main(String[] args) {
        // Create a car with all optional features
        Car car1 = new Car.CarBuilder("V8", "Sedan")
                .setGPS(true)
                .setSunroof(true)
                .setAirbags(true)
                .build();

        System.out.println(car1);  // Outputs: Car [Engine=V8, Model=Sedan, GPS=true, Sunroof=true, Airbags=true]

        // Create a car with only mandatory features
        Car car2 = new Car.CarBuilder("V6", "SUV")
                .build();

        System.out.println(car2);  // Outputs: Car [Engine=V6, Model=SUV, GPS=false, Sunroof=false, Airbags=false]

        // Create a car with some optional features
        Car car3 = new Car.CarBuilder("V8", "Coupe")
                .setGPS(true)
                .build();

        System.out.println(car3);  // Outputs: Car [Engine=V8, Model=Coupe, GPS=true, Sunroof=false, Airbags=false]
    }
}
```

### **Explanation of Usage:**

1. **Chained Method Calls**: The builder allows for chained method calls (e.g., `setGPS(true)`, `setSunroof(true)`), which makes the object construction process concise and readable.
2. **Flexibility**: You can create a car with any combination of features by using or omitting the optional setter methods in the builder.
3. **Immutable Car Object**: Once the car object is built, its attributes cannot be changed, ensuring immutability.

> We can validate our logic in `build()` method



