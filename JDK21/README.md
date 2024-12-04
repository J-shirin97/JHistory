# JDK 21 - Key Features and Enhancements  

## Introduction  

Released on September 19, 2023, JDK 21 is a **Long-Term Support (LTS)** release, making it a significant milestone in the Java platform's evolution. This release introduces several features that have graduated from preview and incubator stages, such as **Record Patterns**, **Pattern Matching for switch**, and **Virtual Threads**, alongside new preview features like **String Templates** and **Unnamed Patterns and Variables**. JDK 21 also focuses on improving runtime performance with features like **Generational ZGC** and expanding API capabilities.  

---

## Key Features  

### Language Features  

- **JEP 430: [String Templates](String%20Templates.md) (Preview)**  
  - Introduced string templates for safer and more readable dynamic string construction, reducing errors and improving clarity.  

- **JEP 440: Record Patterns**  
  - Finalized support for record patterns, enabling concise deconstruction and matching of record components.  

- **JEP 441: Pattern Matching for `switch`**  
  - Finalized pattern matching for `switch`, providing a powerful and expressive way to control flow based on complex conditions.  

- **JEP 443: Unnamed Patterns and Variables (Preview)**  
  - Added unnamed patterns (`_`) and variables to ignore components in patterns concisely.  

- **JEP 445: Unnamed Classes and Instance Main Methods (Preview)**  
  - Simplified prototyping and scripting by allowing unnamed classes and instance-based entry points.  

---

### JVM and Runtime Enhancements  

- **JEP 444: Virtual Threads**  
  - Finalized Virtual Threads, enabling highly scalable and simplified concurrency by decoupling threads from OS resources.  

- **JEP 453: Structured Concurrency (Preview)**  
  - Enhanced structured concurrency to improve error handling, cancellation, and management of concurrent tasks.  

- **JEP 439: Generational ZGC**  
  - Improved the Z Garbage Collector with generational support, optimizing memory management for long-lived and short-lived objects.  

- **JEP 446: Scoped Values (Preview)**  
  - Added Scoped Values, providing a safer alternative to thread-local variables for immutable data sharing.  

---

### Core Libraries and APIs  

- **JEP 431: Sequenced Collections**  
  - Introduced new collection interfaces, like `SequencedSet` and `SequencedMap`, that maintain insertion order and allow bidirectional traversal.  

- **JEP 442: Foreign Function & Memory API (Third Preview)**  
  - Continued refinement of the Foreign Function & Memory API, enhancing Java's interaction with native code and memory.  

- **JEP 448: Vector API (Sixth Incubator)**  
  - Further evolved the Vector API for SIMD computations, improving data-parallel processing capabilities.  

- **JEP 452: Key Encapsulation Mechanism API**  
  - Added cryptographic APIs for key encapsulation, simplifying secure key exchanges.  

---

### Deprecations and Removals  

- **JEP 449: Deprecate the Windows 32-bit x86 Port for Removal**  
  - Deprecated support for the 32-bit Windows x86 port, signaling its eventual removal in a future release.  

- **JEP 451: Prepare to Disallow the Dynamic Loading of Agents**  
  - Introduced restrictions to disallow dynamically loading agents by default, enhancing JVM security.  
