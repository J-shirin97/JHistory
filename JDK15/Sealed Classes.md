# Sealed Classes in Java  

## Introduction  

**Sealed Classes**, introduced as a preview feature in Java 15 (JEP 360) and finalized in Java 17, allow developers to control which classes or interfaces can extend or implement a given class or interface. By restricting inheritance, sealed classes provide a clear and predictable hierarchy, enhancing maintainability and design. Sealed classes work well with other modern features like pattern matching, records, and switch expressions, creating a cohesive system for modeling data.  


## Why Do We Need Sealed Classes?  

1. **Control Over Class Hierarchies**:  
   - In traditional object-oriented design, any class can be extended unless explicitly marked as `final`. This openness can lead to unintended or unsafe subclassing.  

2. **Enhanced Design and Maintainability**:  
   - Sealed classes allow API authors to define a fixed set of subclasses, ensuring the design remains predictable and easier to maintain.  

3. **Improved Pattern Matching and Switches**:  
   - By limiting subclass hierarchies, sealed classes work seamlessly with pattern matching and exhaustive `switch` expressions, making them more robust.  

4. **Prevent Misuse**:  
   - Prevents unauthorized extensions, ensuring subclasses adhere to the intended design.  


## How We Managed Before Sealed Classes  

Before sealed classes, controlling class hierarchies required a combination of `final`, package-private, or protected constructors, which could be cumbersome and less explicit.  

### Example: Restricting Subclasses Manually  

```java
public class Shape {
    private Shape() {} // Prevents public instantiation

    public static class Circle extends Shape {}
    public static class Rectangle extends Shape {}
}
```


#### Issues with the Old Approach:

1)    Requires additional code to enforce restrictions.
2)    Can be bypassed by placing subclasses in the same package.
 3)   Design intent is not immediately clear.

### Using Sealed Classes

Sealed classes allow you to explicitly declare the permitted subclasses using the permits keyword. Only the specified subclasses can extend the sealed class.
Syntax
```java
public sealed class Shape permits Circle, Rectangle, Triangle {}

public final class Circle extends Shape {}
public final class Rectangle extends Shape {}
public final class Triangle extends Shape {}
```

### Features of Sealed Classes

1) Keyword sealed:
        Declares a class or interface as sealed.

2) Permitted Subclasses:
        Defined using the permits clause in the sealed class declaration.

3) Modifiers for Subclasses:
        A sealed class's direct subclasses must be declared as one of the following:
            3.1 final: Prevents further subclassing.
            3.2 sealed: Continues the sealed hierarchy.
            3.2 non-sealed: Opens the class for further inheritance.

Examples
Example 1: Modeling Shapes
```java
public sealed class Shape permits Circle, Rectangle, Triangle {}

public final class Circle extends Shape {
    double radius;
}

public final class Rectangle extends Shape {
    double width, height;
}

public final class Triangle extends Shape {
    double base, height;
}
```
Example 2: Using Pattern Matching with Sealed Classes
```java
public class Main {
    public static void printShapeDetails(Shape shape) {
        if (shape instanceof Circle c) {
            System.out.println("Circle with radius: " + c.radius);
        } else if (shape instanceof Rectangle r) {
            System.out.println("Rectangle with width: " + r.width + " and height: " + r.height);
        } else if (shape instanceof Triangle t) {
            System.out.println("Triangle with base: " + t.base + " and height: " + t.height);
        }
    }
}
```
Example 3: Using Switch Expressions
```java
public class Main {
    public static String describeShape(Shape shape) {
        return switch (shape) {
            case Circle c -> "Circle with radius: " + c.radius;
            case Rectangle r -> "Rectangle with width: " + r.width + " and height: " + r.height;
            case Triangle t -> "Triangle with base: " + t.base + " and height: " + t.height;
        };
    }
}
```
### Real-Life Scenarios

1) Domain Modeling:
        Use sealed classes to represent domain models with a fixed set of possible types, such as payment methods (CreditCard, PayPal, BankTransfer).

2) State Machines:
        Represent a finite set of states in a state machine (e.g., Open, Closed, Processing).

3) API Design:
        Ensure API users can only extend permitted subclasses, maintaining design consistency.

### Advantages of Sealed Classes

1) Explicit Design:
        Clearly defines permitted subclasses, improving code readability and intent.

2)  Safer Inheritance:
        Prevents misuse or unintended subclassing.

3) Better Integration with Modern Features:
        Works seamlessly with pattern matching and switch expressions.

4)  Simplifies Maintenance:
        Reduces the cognitive load by limiting the extension possibilities.

### Limitations

1) Restricted Extensibility:
        Subclasses must be declared in the same module or package, limiting flexibility.

2)  No Runtime Enforcements:
        Sealed classes are enforced at compile time but not dynamically.

### Conclusion

Sealed classes provide a powerful mechanism for controlling inheritance, improving the maintainability and safety of Java applications. They simplify domain modeling, enhance pattern matching, and ensure a clean and predictable class hierarchy. By leveraging sealed classes, developers can write clearer, safer, and more expressive code.