# Text Blocks in Java

## Introduction

Text Blocks, introduced as a preview feature in Java 13 (JEP 355) and finalized in Java 15, simplify the process of writing multi-line string literals. They allow developers to define strings that span multiple lines while preserving readability, eliminating the need for complex string concatenations or escape sequences.

---

## Why Do We Need Text Blocks?

1. **Improve Readability**:

   - Traditional multi-line strings require concatenation and escape characters for special symbols like quotes and newlines. This can make the code hard to read and maintain.
2. **Reduce Boilerplate**:

   - Text Blocks eliminate the need for explicitly adding `\n` for newlines or `\"` for quotes, resulting in cleaner code.
3. **Maintain Formatting**:

   - Text Blocks preserve the natural formatting of the text, which is particularly useful for embedding JSON, HTML, XML, or SQL queries directly into the code.

---

## How We Managed Before Text Blocks

Before Text Blocks, developers used concatenation or escape sequences for multi-line strings.

```java
String json = "{\n" +
              "  \"name\": \"John\",\n" +
              "  \"age\": 30,\n" +
              "  \"city\": \"New York\"\n" +
              "}";
System.out.println(json);
```

Issues:

1)    Verbose and hard to read.
2)    Errors are more likely when adding escape sequences or concatenating lines.


  ###  Using Text Blocks

With Text Blocks, multi-line strings are defined using triple double quotes ("""). The formatting is preserved, and special characters like newlines and quotes don't require escaping.
Example: Creating the Same JSON String

```java
String json = """
    {
      "name": "John",
      "age": 30,
      "city": "New York"
    }
    """;
System.out.println(json);
```


#### Benefits:

1)    The structure is more readable and closely resembles the intended output.
2)    No need for escape sequences or manual newlines.

### Syntax and Rules

 1)   Delimiters:
        Start and end the text block with triple double quotes (""").

2)    Line Breaks:
        Line breaks in the text block correspond directly to line breaks in the string.

 3)   Whitespace Management:
        Leading spaces common to all lines are automatically removed.


    
##    Examples

#### Example 1: Embedding HTML

```java
String html = """
    <html>
        <body>
            <h1>Welcome to Text Blocks</h1>
            <p>This feature simplifies string handling in Java.</p>
        </body>
    </html>
    """;
System.out.println(html);
```

#### Example 2: Writing SQL Queries

```java
String query = """
    SELECT id, name, age
    FROM users
    WHERE age > 30
    ORDER BY age DESC;
    """;
System.out.println(query);
```

#### Example 3: Multi-Line Error Messages

```java
String errorMessage = """
    Error: Invalid Input
    Please check the following:
      - Ensure all fields are filled.
      - Input must be a valid email address.
      - Password must be at least 8 characters long.
    """;
System.out.println(errorMessage);
```

### Real-Life Scenarios

1) Database Queries:
        Simplify embedding complex SQL queries directly into Java code.

2)  Configuration Files:
        Define JSON, XML, or YAML configurations more naturally.

3) Error Handling:
        Create readable multi-line error messages for logs or UI display.

4)  Templates:
        Embed HTML, Markdown, or text templates for emails or reports.

### Advantages of Text Blocks

1) Readability:
        Closely matches the structure of the actual text.

2)  Maintenance:
        Easier to edit and maintain complex strings like JSON or SQL.

3) Error Reduction:
        Reduces errors caused by escaping characters or incorrect concatenations.

4)  Consistency:
        Automatically trims unnecessary leading spaces.

### Conclusion

Text Blocks modernize string handling in Java, making it simpler, more readable, and less error-prone. They are particularly useful for embedding structured text like JSON, HTML, or SQL, and reduce the effort required to manage multi-line strings. By adopting Text Blocks, developers can write cleaner and more maintainable code while reducing boilerplate and potential errors.