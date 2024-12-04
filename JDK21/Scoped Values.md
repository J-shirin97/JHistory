# Scoped Values in Java  

## Introduction  

**Scoped Values**, introduced as an incubator feature in JDK 20 (JEP 429) and previewed in JDK 21 (JEP 446), provide an efficient and thread-safe mechanism for sharing immutable data across threads or within specific code regions. They offer a modern alternative to thread-local variables, enhancing safety and reducing complexity in concurrent programming.  

---

## Why Do We Need Scoped Values?  

1. **Thread-Local Variables Are Error-Prone**:  
   - Thread-local variables are mutable and can lead to unintended side effects if not carefully managed.  

2. **Improved Immutability**:  
   - Scoped Values emphasize immutability, ensuring that data cannot be accidentally modified, improving thread safety.  

3. **Context Propagation**:  
   - Propagating contextual data like user information, logging metadata, or configuration settings across threads is cumbersome with existing methods. Scoped Values simplify this process.  

4. **Efficient Resource Usage**:  
   - Scoped Values are optimized for modern concurrency frameworks like virtual threads, reducing memory overhead compared to thread-local variables.  

---

## How We Managed Before Scoped Values  

Before Scoped Values, developers often relied on:  

### 1. Thread-Local Variables  

Thread-local variables allow data to be tied to a specific thread.  

```java
public class Main {
    private static final ThreadLocal<String> userContext = new ThreadLocal<>();

    public static void main(String[] args) {
        userContext.set("Alice");
        System.out.println("User: " + userContext.get());
        userContext.remove(); // Must be manually cleared
    }
}
```

### Issues:

 1)   Thread-local variables are mutable, increasing the risk of accidental data corruption.
 2)   Manual cleanup is required to prevent memory leaks.

### 2. Passing Context Explicitly

Developers pass context objects explicitly between methods.
```java
public class Main {
    public static void main(String[] args) {
        String user = "Alice";
        processUser(user);
    }

    public static void processUser(String user) {
        System.out.println("Processing user: " + user);
    }
}
```
## Issues:

 1)   Verbose and error-prone in complex applications with deep call chains.

## Using Scoped Values

Scoped Values allow developers to define immutable data and make it accessible within a specific scope, including across threads.
Syntax

Scoped Values are created using ScopedValue and are bound to a specific scope using ScopedValue.where().
### Example: Scoped Values Basics

```java
import jdk.incubator.concurrent.ScopedValue;

public class Main {
    private static final ScopedValue<String> USER_CONTEXT = ScopedValue.newInstance();

    public static void main(String[] args) {
        ScopedValue.where(USER_CONTEXT, "Alice", () -> {
            System.out.println("User: " + USER_CONTEXT.get());
        });
    }
}
```
Output:

User: Alice

## Examples
### Example 1: Context Propagation in Concurrent Applications

Scoped Values seamlessly propagate context across threads, even with virtual threads.
```java
import jdk.incubator.concurrent.ScopedValue;
import java.util.concurrent.Executors;

public class Main {
    private static final ScopedValue<String> USER_CONTEXT = ScopedValue.newInstance();

    public static void main(String[] args) {
        try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
            ScopedValue.where(USER_CONTEXT, "Alice", () -> {
                executor.submit(() -> System.out.println("User: " + USER_CONTEXT.get()));
                executor.submit(() -> System.out.println("User: " + USER_CONTEXT.get()));
            });
        }
    }
}
```
Output:

User: Alice
User: Alice

### Example 2: Logging with Scoped Values

Scoped Values can pass contextual information like request IDs to log statements.
```
import jdk.incubator.concurrent.ScopedValue;

public class Main {
    private static final ScopedValue<String> REQUEST_ID = ScopedValue.newInstance();

    public static void main(String[] args) {
        ScopedValue.where(REQUEST_ID, "12345", () -> {
            log("Processing request");
        });
    }

    public static void log(String message) {
        System.out.println("Request ID: " + REQUEST_ID.get() + " - " + message);
    }
}
```
Output:

Request ID: 12345 - Processing request

### Example 3: Nested Scoped Values

Scoped Values can be nested for layered contexts.
```java
import jdk.incubator.concurrent.ScopedValue;

public class Main {
    private static final ScopedValue<String> USER_CONTEXT = ScopedValue.newInstance();
    private static final ScopedValue<String> SESSION_ID = ScopedValue.newInstance();

    public static void main(String[] args) {
        ScopedValue.where(USER_CONTEXT, "Alice", () -> {
            ScopedValue.where(SESSION_ID, "abc123", () -> {
                System.out.println("User: " + USER_CONTEXT.get());
                System.out.println("Session: " + SESSION_ID.get());
            });
        });
    }
}
```
Output:

User: Alice
Session: abc123

## Advantages of Scoped Values

1) Immutable by Design:
Scoped Values ensure immutability, reducing the risk of accidental modifications.

2) Cleaner Code:
Simplifies passing contextual data without verbose method signatures or manual cleanup.

3) Seamless Thread Integration:
Works efficiently with both traditional and virtual threads.

4) Nestable Scopes:
Supports hierarchical or nested contexts, enabling layered data propagation.

## Limitations

1) Preview/Incubator Feature:
As of JDK 21, Scoped Values are still a preview feature and subject to change.

2) Limited Use Cases:
Scoped Values are specifically designed for immutable context sharing and are not a general-purpose data sharing tool.

## Real-Life Scenarios

1) Web Applications:
Propagate user or request-specific data across multiple service layers.

2) Logging Frameworks:
Pass metadata like request IDs or session information to log entries.

3) Concurrent Batch Processing:
Share configuration or runtime data across virtual threads in parallel processing tasks.

## Conclusion

Scoped Values address long-standing challenges in context propagation and thread safety by providing an immutable, efficient, and modern alternative to thread-local variables. They simplify concurrent programming, enhance code clarity, and work seamlessly with virtual threads. As a key tool for modern Java applications, Scoped Values pave the way for safer and more maintainable concurrent code.