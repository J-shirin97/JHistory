# Records in Java  

## Introduction  

**Records**, introduced in Java 14 as a preview feature (JEP 359) and finalized in Java 16, are a special kind of class in Java designed to model immutable data. Records automatically generate boilerplate code for common tasks like defining fields, constructors, `equals()`, `hashCode()`, and `toString()`. They simplify the creation of data carrier classes, allowing developers to focus on the core business logic rather than repetitive coding.


## Why Do We Need Records?  

1. **Reduce Boilerplate**:  
   - Traditional Java classes require manually implementing constructors, accessors, and methods like `equals()`, `hashCode()`, and `toString()` even for simple data objects.  

2. **Improve Readability**:  
   - Records provide a concise and declarative syntax, making the intent of the code clearer.  

3. **Ensure Immutability**:  
   - Records are immutable by design, reducing bugs related to accidental modifications of state.  

4. **Modernize Java**:  
   - Records align Java with modern programming practices seen in other languages like Kotlin (data classes) and Python (dataclasses).


## How We Managed Before Records  

Before records, developers had to define full classes to represent data objects, even for simple use cases.  

### Example: Traditional Data Class  

```java
public class Person {
    private final String name;
    private final int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Person person = (Person) o;
        return age == person.age && name.equals(person.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }
}
```

### Issues with the Old Approach:

 1)   Verbose: A simple data class requires significant boilerplate.
 2)   Error-Prone: Manually implementing methods like equals() and hashCode() can introduce bugs.




 ### Using Records

With records, the same functionality can be achieved with significantly less code.
Example: Defining a Record
```java
public record Person(String name, int age) {}
```
Benefits:

 1)   All fields are automatically private and final.
  2)  A canonical constructor, accessors, and methods like equals(), hashCode(), and toString() are generated automatically.

Features of Records

  1) Canonical Constructor:
        Records generate a constructor that initializes all fields in the order they are declared.

   2) Accessors:
        Records automatically provide getter methods for each field, named after the field itself.

3)    Immutability:
        Fields of a record are implicitly final, ensuring immutability.

  4)  Compact Syntax:
        Records reduce boilerplate while maintaining the full functionality of a traditional class.

Examples
Example 1: Representing a Data Object
```java
public record Employee(String name, String department, double salary) {}

public class Main {
    public static void main(String[] args) {
        Employee emp = new Employee("Alice", "HR", 75000);
        System.out.println(emp.name()); // Accessor
        System.out.println(emp); // toString()
    }
}
```
Example 2: Using Records in Collections
```java
import java.util.List;

public record Product(String name, double price) {}

public class Main {
    public static void main(String[] args) {
        List<Product> products = List.of(
            new Product("Laptop", 999.99),
            new Product("Smartphone", 699.99)
        );

        products.forEach(System.out::println);
    }
}
```
Example 3: Custom Methods in Records

Records allow custom methods, but their fields remain final.
```java
public record Circle(double radius) {
    public double area() {
        return Math.PI * radius * radius;
    }
}
```

### Limitations of Records

1) No Custom Setters:
        Fields in records are immutable, so you cannot add setters.

2) Inheritance:
        Records cannot extend other classes but can implement interfaces.

3)    Serialization:
        Records are not inherently serializable; you must explicitly implement Serializable if required.

### Real-Life Scenarios

 1)   Data Transfer Objects (DTOs):
        Use records to model immutable objects exchanged between APIs or services.

 2)   Configuration Classes:
        Define simple, immutable configuration objects for frameworks or applications.

  3)  Logging and Debugging:
        Use records to represent structured log messages or debug information.

### Advantages of Using Records

  1)   Conciseness:
        Reduces boilerplate code for common data classes.

  2)  Readability:
        Clearly communicates the purpose of the class as a data carrier.

   3)   Immutability:
        Encourages immutable design, reducing potential bugs related to state changes.

4)  Integration with Modern Java:
        Works seamlessly with features like Streams, Collections, and Pattern Matching.

### Conclusion

Records are a powerful addition to Java for simplifying the creation of data-centric classes. They promote immutability, reduce boilerplate code, and improve readability, making them ideal for modern application development. By adopting records, developers can focus on business logic while benefiting from clean, concise, and maintainable code.