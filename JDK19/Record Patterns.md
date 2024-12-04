# JEP 405: Record Patterns (Preview)  

## Introduction  

**Record Patterns**, introduced as a preview feature in JDK 19 (JEP 405), extend pattern matching by enabling deconstruction of record objects. They allow developers to extract values from record components directly within patterns, simplifying and enhancing data-centric programming. This feature integrates seamlessly with existing features like `switch` expressions and pattern matching for `instanceof`, enabling more concise, readable, and maintainable code.  

---

## Why Do We Need Record Patterns?  

1. **Simplified Data Extraction**:  
   - Without record patterns, extracting data from record objects involves boilerplate code to call accessor methods and assign their results to local variables.  

2. **Improved Readability**:  
   - Record patterns allow deconstruction directly within the pattern, making the intent of the code clearer and reducing verbosity.  

3. **Enhanced Integration with Pattern Matching**:  
   - Record patterns work well with `switch` and `instanceof`, allowing more expressive control flow and data processing.  

4. **Facilitates Immutability**:  
   - Records, which are immutable by design, pair naturally with pattern matching for safe and concise data processing.  

---

## How We Managed Before Record Patterns  

Before record patterns, developers had to manually extract components from record objects using accessors and write additional logic to check object types.  

### Example: Extracting Data from Records Manually  

```java
public record Person(String name, int age) {}

public class Main {
    public static void main(String[] args) {
        Person person = new Person("Alice", 30);

        if (person != null && person instanceof Person) { // Type check
            String name = person.name(); // Extract data manually
            int age = person.age();

            if (age > 18) {
                System.out.println(name + " is an adult.");
            }
        }
    }
}
```

### Issues with the Old Approach:

 1)   Boilerplate: Requires repetitive calls to accessors and manual type checks.
  2)  Verbosity: Obscures the core logic with excessive syntax.

### Using Record Patterns

Record patterns allow deconstruction directly within the if or switch statements, enabling concise and expressive code.
Syntax:

```java
if (object instanceof RecordType(ComponentType1 name, ComponentType2 age)) {
    // Deconstructed components are directly accessible
}
```

Example: Simplified Data Extraction
```java
public record Person(String name, int age) {}

public class Main {
    public static void main(String[] args) {
        Person person = new Person("Alice", 30);

        if (person instanceof Person(String name, int age) && age > 18) {
            System.out.println(name + " is an adult.");
        }
    }
}
```
## Examples

### Example 1: Using Record Patterns with switch

```java
public record Person(String name, int age) {}

public class Main {
    public static void main(String[] args) {
        Person person = new Person("Bob", 20);

        String message = switch (person) {
            case Person(String name, int age) when age >= 18 -> name + " is an adult.";
            case Person(String name, int age) -> name + " is a minor.";
            default -> "Unknown person.";
        };

        System.out.println(message);
    }
}
```
### Example 2: Combining Nested Patterns

Record patterns can be nested within other patterns, enabling deconstruction of hierarchical data structures.

```java
public record Address(String city, String country) {}
public record Person(String name, int age, Address address) {}

public class Main {
    public static void main(String[] args) {
        Person person = new Person("Alice", 30, new Address("Paris", "France"));

        if (person instanceof Person(String name, int age, Address(String city, String country))) {
            System.out.println(name + " lives in " + city + ", " + country);
        }
    }
}
```

## Real-Life Scenarios

  1)  Data Processing Pipelines:
        Simplify extraction and processing of records from structured data formats like JSON or XML.

   2) Domain-Specific Logic:
        Easily implement business rules based on properties of domain objects like Order, Customer, or Product.

   3) Hierarchical Data:
        Efficiently handle nested data structures, such as those in graph processing or configuration parsing.

## Advantages of Record Patterns

1)    Conciseness:
        Eliminates boilerplate code for extracting data from records.

2)    Readability:
        Makes the intent of the code clear by embedding data extraction directly in the control flow.

3)    Expressive Power:
        Combines seamlessly with switch, pattern matching, and nested patterns for advanced data processing.

 4)   Immutable Data:
        Works naturally with Java's immutable records, promoting functional programming practices.

## Limitations

 1)   Preview Feature:
        As of JDK 19, record patterns are a preview feature and may undergo further refinement.

 2)   Limited to Records:
        Only applicable to record types, not standard classes.

## Conclusion

Record patterns revolutionize how Java handles data processing by integrating deconstruction directly into patterns. They reduce boilerplate, improve readability, and enhance expressiveness, making them invaluable for data-driven applications. By leveraging record patterns, developers can write cleaner, safer, and more efficient code, especially in scenarios involving complex data structures or domain modeling.