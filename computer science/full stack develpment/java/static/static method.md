A [[static method]] belongs to the class rather than any specific instance of the class. It can be called without creating an instance of the class and can only access static members (fields or methods).
```java
class MyClass {
    static void myStaticMethod() {
        System.out.println("This is a static method");
    }
}
```
**Key Points**:

- Static methods can be called using the class name, without creating an [[object]]: `MyClass.myStaticMethod()`.
- They can **only access static data members** (variables and methods) and cannot access instance variables or methods.
- They are used mainly for utility or helper methods, such as `Math.max()` or `Collections.sort()`.
```java
class Calculator {
    // Static method to add two numbers
    static int add(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        int sum = Calculator.add(10, 20);  // Calling static method
        System.out.println("Sum: " + sum);  // Output: Sum: 30
    }
}
```
