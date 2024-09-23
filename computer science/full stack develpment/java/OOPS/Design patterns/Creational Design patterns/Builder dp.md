
### **Problem Statement for the [[Builder dp]]:**

In traditional object creation we use constructor. While using constructor we need to specify all the parameter. consider that we have mandatory and optional attributes, So in that case we need to create a different type of constructor respectively. 

### **Example Problem Statement:**

Imagine you are tasked with designing a system to build cars. A `Car` object has many optional and mandatory attributes, such as:

- Mandatory attributes: `engine`, `model`, `wheels`
- Optional attributes: `sunroof`, `GPS`, `airbags`

Constructing a `Car` object with all these fields would require a large constructor with many arguments, most of which may be null if they are optional. This leads to:

- **Confusing Code**: Users of the `Car` class will need to remember the order and type of constructor parameters, which is error-prone.
- **Constructor Overload**: You would need several constructors to account for different configurations of the car, leading to too many overloaded constructors, which becomes difficult to maintain.

**Solution**: Use the **Builder Pattern** to allow users to construct the `Car` object step by step, making the code more readable and easier to maintain. The builder can handle optional parameters gracefully while ensuring mandatory fields are set before the object is built.

### **When to Use the Builder Pattern:**

1. When an object requires many attributes (some mandatory, some optional).
2. When the order of setting attributes can vary.
3. When you want to make the object immutable (i.e., its state cannot change after creation).

[[with and without builder pattern]]