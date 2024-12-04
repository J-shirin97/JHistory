# Try-With-Resources in Java

## Introduction  

The **try-with-resources** statement was introduced in Java 7 as part of Project Coin. It is a specialized form of the `try` statement designed to simplify resource management and improve code readability and reliability. Resources like file streams, database connections, or sockets need to be explicitly closed after use to avoid resource leaks, which is often tedious and error-prone. Try-with-resources automates this process by ensuring resources are closed automatically.

---

## Why Do We Need Try-With-Resources?  

Before the try-with-resources construct, developers had to manage resources manually by explicitly calling their `close()` methods. This manual approach had several drawbacks:

1. **Verbose Code**:  
   Closing resources required repetitive boilerplate code, often nested within `finally` blocks.  

2. **Error-Prone**:  
   Developers might forget to close resources, leading to resource leaks.  

3. **Exception Masking**:  
   Exceptions thrown while closing a resource in a `finally` block could hide exceptions thrown during the main logic.

---

## How We Managed Resources Before Try-With-Resources  

### Using `try-finally`  
The traditional way to manage resources was to open resources in a `try` block and close them in a `finally` block.  

Example: Reading a File (Before Try-With-Resources)  
```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        BufferedReader reader = null;
        try {
            reader = new BufferedReader(new FileReader("file.txt"));
            String line = reader.readLine();
            System.out.println(line);
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (reader != null) {
                try {
                    reader.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```

#### Issues with try-finally:

1)    Nested try-catch blocks in finally make the code verbose.
 2)   Forgetting to close the resource leads to resource leaks.
   3) Errors in closing the resource might overshadow the original exception.

 ##  The Try-With-Resources Solution

With try-with-resources, resources are automatically closed at the end of the try block. The resources must implement the AutoCloseable interface, which includes a single method: close().
How It Works:

-    You declare and initialize the resource inside the try statement.
 -   The JVM automatically closes the resource when the block exits, whether normally or via an exception.

Example: Reading a File (With Try-With-Resources)

```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        try (BufferedReader reader = new BufferedReader(new FileReader("file.txt"))) {
            String line = reader.readLine();
            System.out.println(line);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```

### Advantages of Try-With-Resources
1) ##### Concise Code:
Eliminates the need for explicit finally blocks, reducing boilerplate code.

2) ##### Automatic Resource Management:
Ensures that resources are properly closed, even if an exception is thrown.

3) ##### Improved Exception Handling:
If exceptions occur during both the main logic and resource closure, the main exception is preserved, and the suppression mechanism tracks additional exceptions.


### Real-Life Scenarios
1. ##### File I/O

Reading or writing to files often involves resources like FileReader, BufferedReader, or FileWriter.

```java
try (BufferedReader reader = new BufferedReader(new FileReader("data.txt"))) {
    reader.lines().forEach(System.out::println);
}
```


2. ##### Database Connections

Database connections must be closed after use to release resources.
```java
try (Connection connection = DriverManager.getConnection(DB_URL, USER, PASS);
     Statement statement = connection.createStatement();
     ResultSet resultSet = statement.executeQuery("SELECT * FROM users")) {
    while (resultSet.next()) {
        System.out.println(resultSet.getString("name"));
    }
}
```


3. ##### Network Sockets

Managing sockets for communication also benefits from try-with-resources.

```java
try (Socket socket = new Socket("localhost", 8080);
     PrintWriter out = new PrintWriter(socket.getOutputStream(), true)) {
    out.println("Hello, Server!");
}
```


#### Multiple Resources in Try-With-Resources

You can manage multiple resources in a single try-with-resources statement by separating their declarations with semicolons.

Example: Reading and Writing Files Simultaneously

```java
try (BufferedReader reader = new BufferedReader(new FileReader("input.txt"));
     BufferedWriter writer = new BufferedWriter(new FileWriter("output.txt"))) {
    String line;
    while ((line = reader.readLine()) != null) {
        writer.write(line);
        writer.newLine();
    }
}
```


### How to Use Custom Resources

To use custom objects with try-with-resources, your class must implement the AutoCloseable interface and override the close() method.

Example: Custom Resource Management

``` java
class MyResource implements AutoCloseable {
    @Override
    public void close() {
        System.out.println("Resource closed!");
    }
}

public class Main {
    public static void main(String[] args) {
        try (MyResource resource = new MyResource()) {
            System.out.println("Using resource...");
        }
    }
}
```


### Conclusion

Try-with-resources is a powerful feature that simplifies resource management in Java. It eliminates boilerplate code, prevents resource leaks, and ensures clean, concise, and robust error handling. By leveraging this feature, developers can focus more on application logic and less on managing resources manually.