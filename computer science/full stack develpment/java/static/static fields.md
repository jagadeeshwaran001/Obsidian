A [[static field]] is a class-level variable that is shared by all instances of the class. It is initialized when the class is loaded into memory and exists as long as the class is loaded. Static variables are not tied to any specific object instance but are common to all instances of the class.

```java
class MyClass {
    static int myStaticVar = 5;  // Static variable
}
```

**Key Points**:

- Only one copy of the static variable exists, and all instances of the class share it.
- Static variables are initialized only once, at class loading time.
- Static variables can be accessed directly by the class name: `MyClass.myStaticVar`.
- Memory for static variables is allocated in a special memory area known as the **method area**.

```java
class Counter {
    static int count = 0;  // Static variable

    Counter() {
        count++;
        System.out.println("Count: " + count);
    }

    public static void main(String[] args) {
        new Counter();  // Output: Count: 1
        new Counter();  // Output: Count: 2
    }
}
```