# JDK 14 - Key Features and Enhancements  

## Introduction  

Released on March 17, 2020, JDK 14 brought several enhancements across the language, JVM, and runtime libraries. This release continued the preview and incubator approach, introducing features like **Records**, **Pattern Matching for `instanceof`**, and the **Foreign-Memory Access API** for testing and feedback. It also finalized **Switch Expressions**, previously a preview feature, and included multiple performance and usability updates.

---

## Key Features  

### Language Features  

- **JEP 305: Pattern Matching for [instanceof](instanceof.md) (Preview)**  
  - Simplified type checks and casting by integrating pattern matching into the `instanceof` operator.  

- **JEP 359: [Records](Records.md) (Preview)**  
  - Introduced `record` as a special type for modeling immutable data with minimal boilerplate.  

- **JEP 361: Switch Expressions (Standard)**  
  - Finalized **Switch Expressions**, enabling `switch` to be used as both a statement and an expression.  

- **JEP 368: Text Blocks (Second Preview)**  
  - Continued preview of multi-line string literals for improved string handling.  

---

### JVM and Garbage Collection Enhancements  

- **JEP 345: NUMA-Aware Memory Allocation for G1**  
  - Optimized memory allocation on NUMA (Non-Uniform Memory Access) systems for the G1 Garbage Collector.  

- **JEP 364 and JEP 365: ZGC on macOS and Windows**  
  - Extended support for the Z Garbage Collector (ZGC) to macOS and Windows, improving scalability and low-latency performance on these platforms.  

- **JEP 363: Remove the Concurrent Mark-Sweep (CMS) Garbage Collector**  
  - Deprecated the CMS garbage collector in favor of more modern alternatives like G1 and ZGC.  

- **JEP 366: Deprecate the ParallelScavenge + SerialOld GC Combination**  
  - Marked the Parallel Scavenge and Serial Old GC combination for deprecation due to limited use.  

---

### Core Library and Tooling Updates  

- **JEP 343: Packaging Tool (Incubator)**  
  - Introduced a new tool for packaging Java applications as native executables, improving deployment.  

- **JEP 349: JFR Event Streaming**  
  - Enabled continuous monitoring and streaming of Java Flight Recorder (JFR) events for real-time diagnostics.  

- **JEP 352: Non-Volatile Mapped Byte Buffers**  
  - Added support for file mappings to non-volatile memory, improving performance for certain I/O operations.  

- **JEP 358: Helpful NullPointerExceptions**  
  - Enhanced `NullPointerException` messages to include precise details about which variable was `null`.  

---

### Deprecations and Removals  

- **JEP 362: Deprecate Solaris and SPARC Ports**  
  - Marked Solaris and SPARC platforms for removal due to declining usage and support.  

- **JEP 367: Remove the Pack200 Tools and API**  
  - Removed the Pack200 compression tools and API, following their deprecation in earlier versions.  

---

### Experimental and Incubator Features  

- **JEP 370: Foreign-Memory Access API (Incubator)**  
  - Introduced a new API for accessing memory outside the Java heap, enabling high-performance, low-level operations.  
