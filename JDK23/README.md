# JDK 23 - Key Features and Enhancements  

## Introduction  

Released on September 17, 2024, JDK 23 brings several advancements in language features, runtime optimizations, and developer productivity tools. This release continues refining preview and incubator features like **Primitive Types in Patterns**, **Structured Concurrency**, and **Scoped Values**, while introducing new capabilities such as **Markdown Documentation Comments** and default **Generational Mode** for ZGC. Notably, the **String Templates** feature was removed due to design challenges.  

---

## Key Features  

### Language Features  

- **JEP 455: Primitive Types in Patterns, `instanceof`, and `switch` (Preview)**  
  - Enabled pattern matching and `switch` to work seamlessly with primitive types, improving flexibility and consistency in data-oriented control flows.  

- **JEP 476: Module Import Declarations (Preview)**  
  - Simplified module usage by allowing modules to declare imports directly, reducing boilerplate in modular applications.  

- **JEP 482: Flexible Constructor Bodies (Second Preview)**  
  - Enhanced constructors to allow more flexible initialization logic before invoking `super(...)` or `this(...)`.  

---

### JVM and Runtime Enhancements  

- **JEP 474: ZGC: Generational Mode by Default**  
  - Made the generational mode the default for the Z Garbage Collector (ZGC), further optimizing memory management for workloads with a mix of short-lived and long-lived objects.  

- **JEP 471: Deprecate the Memory-Access Methods in `sun.misc.Unsafe` for Removal**  
  - Marked `sun.misc.Unsafe` memory-access methods for future removal, encouraging migration to modern alternatives like the Foreign Function & Memory API.  

---

### Core Libraries and APIs  

- **JEP 466: Class-File API (Second Preview)**  
  - Continued refinement of the Class-File API, simplifying bytecode-level operations for tools and frameworks.  

- **JEP 473: Stream Gatherers (Second Preview)**  
  - Enhanced the `Stream` API with gatherers, improving flexibility and performance for data aggregation tasks.  

- **JEP 467: Markdown Documentation Comments**  
  - Introduced support for writing API documentation in Markdown, modernizing the process of creating and maintaining JavaDoc.  

---

### Experimental and Incubating Features  

- **JEP 469: Vector API (Eighth Incubator)**  
  - Further improved the Vector API for SIMD operations, optimizing data-parallel computations for high-performance applications.  

- **JEP 480: Structured Concurrency (Third Preview)**  
  - Refined structured concurrency for better error handling and task lifecycle management in concurrent programming.  

- **JEP 481: Scoped Values (Third Preview)**  
  - Continued development of Scoped Values, providing a modern and thread-safe alternative to thread-local variables for immutable context sharing.  

- **JEP 477: Implicitly Declared Classes and Instance Main Methods (Third Preview)**  
  - Simplified Java prototyping and scripting workflows with implicit class declarations and instance-based `main` methods.  

---

## Deprecations and Removals  

- **String Templates**:  
  - Removed due to design issues, following two preview iterations.  
