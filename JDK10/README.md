# JDK 10 - Key Features and Enhancements

## Introduction  
Released on March 20, 2018, JDK 10 was the first release under the new **time-based release schedule**, ensuring predictable updates every six months. This version introduced several improvements across the language, runtime, and tools, enhancing developer productivity, performance, and maintainability.

---

## Key Features  

### Language Features  

- **JEP 286: [Local-Variable Type Inference](Local-Variable%20Type%20Inference.md) **  
  - Introduced the `var` keyword, allowing developers to declare local variables with inferred types for cleaner and more concise code.  

---

### JVM and Runtime Enhancements  

- **JEP 304: Garbage-Collector Interface**  
  - Standardized a clean interface for garbage collectors, simplifying the addition of new GC implementations.  

- **JEP 307: Parallel Full GC for G1**  
  - Improved the G1 Garbage Collector by introducing parallelism during full garbage collection, reducing GC pause times.  

- **JEP 310: Application Class-Data Sharing (AppCDS)**  
  - Extended Class-Data Sharing (CDS) to allow application classes to be shared across multiple JVMs, improving startup time and memory usage.  

- **JEP 312: Thread-Local Handshakes**  
  - Enabled more efficient operations on individual threads without stopping all threads, enhancing JVM responsiveness and performance.  

- **JEP 316: Heap Allocation on Alternative Memory Devices**  
  - Allowed the JVM heap to be allocated on non-volatile memory devices, providing flexibility for specialized environments.  

---

### Tools and Build Improvements  

- **JEP 296: Consolidate the JDK Forest into a Single Repository**  
  - Simplified the JDK source code structure by consolidating multiple repositories into a single one.  

- **JEP 313: Remove the Native-Header Generation Tool (`javah`)**  
  - Removed the obsolete `javah` tool, as its functionality was replaced by improved build systems.  

- **JEP 317: Experimental Java-Based JIT Compiler**  
  - Added an experimental Just-In-Time (JIT) compiler based on Graal, enabling enhanced performance for specific workloads.  

---

### Security and Internationalization  

- **JEP 314: Additional Unicode Language-Tag Extensions**  
  - Added support for more Unicode extensions, improving compatibility with internationalized applications.  

- **JEP 319: Root Certificates**  
  - Included a default set of root certificates in the JDK, improving TLS security out of the box.  

---

### Release Management  

- **JEP 322: Time-Based Release Versioning**  
  - Adopted a new versioning scheme based on time, simplifying version numbering and aligning releases with the six-month release cadence.  
