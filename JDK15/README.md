# JDK 15 - Key Features and Enhancements  

## Introduction  

Released on September 15, 2020, JDK 15 introduced several significant updates, including finalized support for **Text Blocks**, production readiness for the **Shenandoah** and **Z Garbage Collectors**, and new language features such as **Sealed Classes** (Preview). This release also removed outdated components like the Nashorn JavaScript Engine and Solaris/SPARC ports, streamlining the Java platform for modern development needs.

---

## Key Features  

### Language Features  

- **JEP 378: [Text Blocks](../JDK13/Text%20Blocks.md)**  
  - Finalized support for multi-line string literals, making it easier to handle formatted text like JSON, HTML, or SQL in code.  

- **JEP 360: [Sealed Classes](Sealed%20Classes.md) (Preview)**  
  - Introduced a way to control which classes or interfaces can extend or implement a class/interface, improving maintainability and design.  

- **JEP 375: [Pattern Matching for `instanceof`](../JDK14/instanceof.md) (Second Preview)**  
  - Continued refinement of pattern matching, simplifying type checks and casts in conditional logic.  

- **JEP 384: [Records](../JDK14/Records.md) (Second Preview)**  
  - Extended the preview of records, focusing on immutable data modeling with reduced boilerplate.  

---

### JVM and Garbage Collection Enhancements  

- **JEP 377: Z Garbage Collector (ZGC)**  
  - Marked the **ZGC** as production-ready, providing low-latency garbage collection suitable for large-scale applications.  

- **JEP 379: Shenandoah Garbage Collector**  
  - Promoted **Shenandoah**, a low-pause-time garbage collector, for production use.  

---

### Core Library and API Updates  

- **JEP 371: Hidden Classes**  
  - Introduced hidden classes, enabling frameworks to define classes that are not discoverable by other classes, useful for dynamic class generation.  

- **JEP 373: Reimplement the Legacy DatagramSocket API**  
  - Modernized the `DatagramSocket` API with a more maintainable implementation.  

- **JEP 383: Foreign-Memory Access API (Second Incubator)**  
  - Continued incubation of the Foreign-Memory Access API, enabling high-performance access to memory outside the Java heap.  

---

### Deprecations and Removals  

- **JEP 372: Remove the Nashorn JavaScript Engine**  
  - Removed the Nashorn JavaScript Engine due to the availability of modern JavaScript runtimes.  

- **JEP 381: Remove the Solaris and SPARC Ports**  
  - Dropped support for Solaris and SPARC platforms to focus on widely-used operating systems.  

- **JEP 385: Deprecate RMI Activation for Removal**  
  - Deprecated the RMI Activation system for eventual removal due to limited usage.  

- **Root CA Certificates**  
  - Removed some root CA certificates from the JDK.  
