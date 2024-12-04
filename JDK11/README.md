# JDK 11 - Key Features and Enhancements

## Introduction

Released on September 25, 2018, JDK 11 is a **Long-Term Support (LTS)** version, offering extended support and stability for enterprise use. This release focuses on enhancing performance, security, and productivity, while also removing outdated components. It includes new APIs, garbage collection improvements, cryptographic enhancements, and support for modern application requirements.

---

## Key Features

### Language and Syntax Improvements

- **JEP 323: Local-Variable Syntax for Lambda Parameters**
  - Extended the `var` keyword to lambda parameters for consistent type inference.

---

### JVM and Runtime Enhancements

- **JEP 181: Nest-Based Access Control**

  - Simplified access control between nested classes, removing the need for synthetic bridge methods.
- **JEP 315: Improve Aarch64 Intrinsics**

  - Enhanced performance for ARM64 (Aarch64) processors by adding new intrinsics.
- **JEP 318: Epsilon: A No-Op Garbage Collector**

  - Introduced a garbage collector that handles memory allocation without reclamation, useful for testing and short-lived applications.
- **JEP 333: Z Garbage Collector (ZGC)**

  - Experimental low-latency garbage collector designed for scalable applications, capable of managing large heaps with minimal pause times.

---

### Library Enhancements

- **JEP 320: Remove Java EE and CORBA Modules**

  - Removed outdated and rarely used modules from the JDK to simplify maintenance.
- **JEP 321: HTTP Client (Standard)**

  - Standardized the HTTP Client API introduced in JDK 9 for handling HTTP/2 and WebSocket communication.
- **JEP 329: ChaCha20 and Poly1305 Cryptographic Algorithms**

  - Added support for modern encryption algorithms for enhanced security.
- **JEP 332: Transport Layer Security (TLS) 1.3**

  - Updated the TLS implementation to the latest version, improving security and performance.

---

### Developer Tools

- **JEP 328: Flight Recorder**

  - Integrated Flight Recorder, a low-overhead data collection framework for troubleshooting and profiling.
- **JEP 330: Launch Single-File Source-Code Programs**

  - Enabled developers to run simple Java programs without prior compilation using the `java` command directly.

---

### Deprecations and Removals

- **JEP 335: Deprecate Nashorn JavaScript Engine**

  - Marked the Nashorn JavaScript Engine for removal due to the availability of modern alternatives.
- **JEP 336: Deprecate the Pack200 Tools and API**

  - Deprecated the Pack200 compression format due to its declining usage.

---
