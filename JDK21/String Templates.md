# String Templates in Java  

## Introduction  

**String Templates**, introduced as a preview feature in JDK 21 (JEP 430), simplify the construction of dynamic strings by embedding expressions directly within a string literal. This feature improves code readability, reduces errors, and integrates seamlessly with Java's type system. String Templates are especially useful in scenarios like constructing SQL queries, HTML content, or logging messages where dynamic values need to be interpolated into string literals.  

---

## Why Do We Need String Templates?  

1. **Verbosity with Current Approaches**:  
   - Current methods like string concatenation (`+`) or `String.format()` are verbose and can lead to hard-to-read and error-prone code.  

2. **Potential for Errors**:  
   - Mixing dynamic and static content often leads to bugs, such as mismatched placeholders in `String.format()` or incorrect concatenation order.  

3. **Lack of Type Safety**:  
   - Existing approaches don't always enforce type safety, leading to runtime errors.  

4. **Integration with External Libraries**:  
   - Simplifying dynamic string construction helps in generating structured data like JSON, SQL, or HTML.  

---

## How We Managed Before String Templates  

Before String Templates, developers typically used string concatenation, `String.format()`, or external libraries like Apache Commons Lang or StringBuilder for dynamic strings.  

### Example: Traditional String Concatenation  

```java
String name = "Alice";
int age = 30;
String message = "Name: " + name + ", Age: " + age;
System.out.println(message);
```
### Example: Using String.format

```java
String name = "Alice";
int age = 30;
String message = String.format("Name: %s, Age: %d", name, age);
System.out.println(message);
```

### Issues with These Approaches:

1)    Concatenation: Difficult to read and maintain with multiple dynamic values.
2)    String.format: Error-prone due to mismatched format specifiers and arguments.
3)    Complexity: Requires external libraries or verbose code for structured output.

## What Are String Templates?

String Templates allow you to embed expressions directly in string literals, enclosed by ${}. The expressions are evaluated at runtime, and their values are interpolated into the string.
Syntax

String msg = STR."Hello, ${name}! You are ${age} years old.";

Key Features:

1)    Interpolation: Directly include variables or expressions within strings.
2)    Type Safety: Expressions are type-checked at compile time.
3)    Improved Readability: Clearly separates static and dynamic content.

## Using String Templates

### Example: Basic Interpolation
```java
String name = "Alice";
int age = 30;

String message = STR."Name: ${name}, Age: ${age}";
System.out.println(message);
// Output: Name: Alice, Age: 30
```

### Example: Embedded Expressions

```java
int length = 5;
int width = 10;

String areaMessage = STR."The area of the rectangle is ${length * width} square units.";
System.out.println(areaMessage);
// Output: The area of the rectangle is 50 square units.
```

## Real-Life Scenarios
### 1. Logging Messages

```java
String user = "admin";
String action = "logged in";

String logMessage = STR."[INFO] User ${user} has ${action}.";
System.out.println(logMessage);
// Output: [INFO] User admin has logged in.
```

### 2. SQL Query Construction

```java
String tableName = "users";
String condition = "age > 30";

String query = STR."SELECT * FROM ${tableName} WHERE ${condition}";
System.out.println(query);
// Output: SELECT * FROM users WHERE age > 30
```

### 3. HTML Content Generation

```java
String title = "Welcome";
String body = "Thank you for visiting our website.";

String html = STR."""
    <html>
        <head><title>${title}</title></head>
        <body>${body}</body>
    </html>
    """;

System.out.println(html);
/*
Output:
<html>
    <head><title>Welcome</title></head>
    <body>Thank you for visiting our website.</body>
</html>
*/
```

## Advantages of String Templates

1) Readability:
Makes dynamic strings easier to read and maintain.

2) Type Safety:
Ensures all embedded expressions are type-checked at compile time.

3) Efficiency:
Reduces boilerplate code, making development faster and less error-prone.

4) Integration with Java Features:
Works seamlessly with other Java features like records, pattern matching, and expressions.

## Limitations

1) Preview Feature:
As of JDK 21, String Templates are a preview feature and may change in future releases.

2) Limited Support for Complex Formatting:
For highly customized formatting, additional methods or libraries may still be required.

## Conclusion

String Templates revolutionize string handling in Java by making dynamic string construction simpler, safer, and more readable. They reduce boilerplate, enhance maintainability, and integrate seamlessly with modern Java features. Whether for logging, SQL query generation, or building structured content, String Templates provide a powerful tool for developers to write cleaner, more efficient code.