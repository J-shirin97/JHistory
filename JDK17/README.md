# JDK 17 - Key Features and Enhancements  

## Introduction  

Released in September 2021, JDK 17 is a **Long-Term Support (LTS)** release, offering extended stability and support for enterprises. This release includes a mix of finalized features and previews, focusing on enhancing the Java language, JVM, and APIs. JDK 17 also simplifies the platform by removing outdated components like RMI Activation and the Applet API, while deprecating the Security Manager for future removal.  

---

## Key Features  

### Language Features  

- **JEP 406: Pattern Matching for `switch` (Preview)**  
  - Extended pattern matching to `switch` statements, enabling more concise and expressive data-oriented control flow.  

- **JEP 409: Sealed Classes**  
  - Finalized sealed classes, allowing developers to restrict which classes or interfaces can extend or implement a given type, improving design and maintainability.  

---

### JVM and Runtime Enhancements  

- **JEP 306: Restore Always-Strict Floating-Point Semantics**  
  - Ensured all floating-point operations in Java are consistently strict, simplifying behavior across platforms.  

- **JEP 356: Enhanced Pseudo-Random Number Generators**  
  - Added new interfaces and implementations for more flexible and performant pseudo-random number generation.  

- **JEP 410: Remove the Experimental AOT and JIT Compiler**  
  - Removed Ahead-of-Time (AOT) and Just-In-Time (JIT) compilers introduced in earlier versions due to limited adoption.  

- **JEP 411: Deprecate the Security Manager for Removal**  
  - Marked the Security Manager for eventual removal due to its declining usage and modern security alternatives.  

---

### Core Libraries and APIs  

- **JEP 412: Foreign Function & Memory API (Incubator)**  
  - Continued development of the Foreign Function and Memory API for safe and efficient interaction with native code and memory outside the JVM.  

- **JEP 414: Vector API (Second Incubator)**  
  - Enhanced the Vector API, providing hardware-accelerated SIMD (Single Instruction, Multiple Data) computations for improved performance in data processing tasks.  

- **JEP 415: Context-Specific Deserialization Filters**  
  - Introduced configurable filters for deserialization, improving application security by limiting deserialization of potentially harmful objects.  

---

### Platform and Tooling Updates  

- **JEP 382: New macOS Rendering Pipeline**  
  - Replaced the existing rendering pipeline on macOS with a new implementation based on the Metal framework for improved graphics performance.  

- **JEP 391: macOS/AArch64 Port**  
  - Added support for running Java on macOS devices with ARM-based (AArch64) processors, like Apple's M1 chips.  

---

### Deprecations and Removals  

- **JEP 398: Deprecate the Applet API for Removal**  
  - Marked the Applet API for future removal due to the obsolescence of applets in modern web browsers.  

- **JEP 407: Remove RMI Activation**  
  - Removed the RMI Activation system, which had been previously deprecated.  

- **JEP 403: Strongly Encapsulate JDK Internals**  
  - Enforced encapsulation of JDK internals, continuing efforts to improve security and modularity by default.  
