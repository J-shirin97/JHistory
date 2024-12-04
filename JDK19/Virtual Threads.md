# Virtual Threads in Java  

## Introduction  

**Virtual Threads**, introduced as a preview feature in JDK 19 (JEP 425), are lightweight threads managed by the Java runtime instead of the operating system. They are designed to simplify concurrent programming by enabling developers to create and manage thousands or even millions of threads efficiently. Virtual Threads decouple the number of threads from the underlying OS threads, making high-throughput concurrent applications more scalable and easier to write.  

---

## Why Do We Need Virtual Threads?  

1. **Traditional Threads Are Expensive**:  
   - Each OS-managed thread requires a significant amount of memory for its stack (typically 1MB) and incurs context-switching overhead, limiting scalability.  

2. **Simpler Concurrency Models**:  
   - Developers often rely on complex constructs like thread pools to manage the limited number of OS threads efficiently. Virtual Threads eliminate the need for such constructs in many scenarios.  

3. **Reactive Programming Complexity**:  
   - Frameworks like Reactor or RxJava use event-driven, non-blocking models to achieve scalability, which can be complex to implement and debug. Virtual Threads allow blocking code to be used without compromising scalability.  

4. **Easier Debugging and Maintenance**:  
   - Virtual Threads maintain a one-to-one mapping between business tasks and threads, making code easier to debug and understand.  

---

## How We Managed Before Virtual Threads  

Before Virtual Threads, developers used:  

1. **OS Threads**:  
   - Directly creating and managing threads using the `Thread` class or `ExecutorService`.  

2. **Thread Pools**:  
   - Limited the number of threads to match available resources, reusing them for multiple tasks.  

3. **Reactive Programming**:  
   - Non-blocking frameworks like Reactor or RxJava to handle concurrency without using many threads.  

### Example: Traditional Thread Pool  

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class Main {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(10);

        for (int i = 0; i < 100; i++) {
            executor.submit(() -> {
                System.out.println(Thread.currentThread().getName() + " is working.");
            });
        }

        executor.shutdown();
    }
}
```

### Issues:

1)    Limited by the size of the thread pool.
 2)   Complex configurations to optimize resource usage.
  3)  Blocking tasks reduce throughput.


 ## Virtual Threads: A Game Changer

Virtual Threads are lightweight threads implemented entirely in the Java runtime. They use a continuation-based model to suspend and resume tasks, freeing the underlying OS thread when the virtual thread is blocked.
Key Features:

1)    Lightweight: Minimal memory overhead, allowing millions of threads to run concurrently.
2)    Non-blocking: Virtual Threads can block without tying up OS resources.
 3)   Backward Compatibility: Works with existing thread-based code.

How to Use Virtual Threads
Creating Virtual Threads

Virtual Threads can be created using the Thread.ofVirtual() factory method.

```java
public class Main {
    public static void main(String[] args) {
        Thread virtualThread = Thread.ofVirtual().start(() -> {
            System.out.println("Hello from a virtual thread!");
        });

        try {
            virtualThread.join();
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
}
```

### Using Virtual Thread Executors

Virtual Threads can also be managed using Executors.newVirtualThreadPerTaskExecutor().
```java
import java.util.concurrent.ExecutorService;

public class Main {
    public static void main(String[] args) {
        try (ExecutorService executor = Executors.newVirtualThreadPerTaskExecutor()) {
            for (int i = 0; i < 1000; i++) {
                executor.submit(() -> {
                    System.out.println(Thread.currentThread().getName() + " is running.");
                });
            }
        }
    }
}
```
## Examples

### Example 1: High-Concurrency Web Server

```java 
import java.io.IOException;
import java.net.ServerSocket;
import java.net.Socket;

public class Main {
    public static void main(String[] args) throws IOException {
        try (ServerSocket serverSocket = new ServerSocket(8080)) {
            while (true) {
                Socket clientSocket = serverSocket.accept();
                Thread.ofVirtual().start(() -> handleClient(clientSocket));
            }
        }
    }

    private static void handleClient(Socket socket) {
        try (socket) {
            var in = socket.getInputStream();
            var out = socket.getOutputStream();
            out.write(("HTTP/1.1 200 OK\r\n\r\nHello, World!").getBytes());
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

### Example 2: Parallel Data Processing

```java
import java.util.List;
import java.util.concurrent.Executors;

public class Main {
    public static void main(String[] args) {
        List<Integer> data = List.of(1, 2, 3, 4, 5);

        try (var executor = Executors.newVirtualThreadPerTaskExecutor()) {
            data.forEach(value -> executor.submit(() -> process(value)));
        }
    }

    private static void process(int value) {
        System.out.println("Processing: " + value + " in " + Thread.currentThread().getName());
    }
}
``` 

## Advantages of Virtual Threads

1) Scalability:
Easily handle millions of concurrent tasks.

2) Simplified Concurrency:
Allows blocking code without sacrificing performance.

3) Easier Debugging:
Maintains a clear one-to-one mapping between tasks and threads.

4) Backward Compatibility:
Works with existing thread-based APIs.

## Limitations

1) Preview Feature:
As of JDK 19, Virtual Threads are a preview feature and subject to changes.

2) Not Suitable for All Workloads:
Tasks requiring tight CPU-bound processing may still need careful resource management.

3) Requires JVM Support:
Older JVM versions do not support Virtual Threads.

## Real-Life Scenarios

1) Web Servers:
Handle a large number of simultaneous connections efficiently.

2) Database Applications:
Manage many blocking I/O operations without thread pool limitations.

3) Parallel Data Processing:
Run data-intensive tasks concurrently with minimal overhead.

## Conclusion

Virtual Threads represent a paradigm shift in Java concurrency, simplifying thread-based programming while delivering unmatched scalability. By enabling developers to write straightforward, high-performance code, Virtual Threads bridge the gap between traditional thread-based programming and modern reactive paradigms. They are poised to transform the way developers build concurrent applications in Java.