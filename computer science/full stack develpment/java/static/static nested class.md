In [[java]] we cannot initialize the [[static]] class like [[c#]]

However, you can have **static nested classes**, which are classes declared inside another class with the `static` keyword.

### Key Points about Static Nested Classes:

- A static nested class is associated with its outer class, and it **cannot access non-static members** (fields or methods) of the outer class directly.
- You **can define a constructor** inside a static nested class, just like any other regular class.
```java
class OuterClass {

    // Static nested class
    static class StaticNestedClass {
        int value;

        // Constructor for the static nested class
        StaticNestedClass(int value) {
            this.value = value;
        }

        void displayValue() {
            System.out.println("Value: " + value);
        }
    }
    
    public static void main(String[] args) {
        // Creating an instance of the static nested class
        StaticNestedClass nestedObj = new StaticNestedClass(100);
        nestedObj.displayValue();  // Output: Value: 100
    }
}
```

