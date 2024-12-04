# JDK 13 - Key Features and Enhancements

## Introduction

Released on September 17, 2019, JDK 13 continued the pattern of delivering incremental improvements to the Java platform under the six-month release cycle. This version introduced several significant features, including enhancements to garbage collection, socket APIs, and new language features like **Switch Expressions** and **Text Blocks**, both as preview features.

---

## Key Features

### Language Features

- **JEP 354: Switch Expressions (Preview)**

  - Enhanced the `switch` statement to support expressions, improving code readability and reducing boilerplate.
- **JEP 355: [Text Blocks](Text%20Blocks.md) (Preview)**

  - Introduced multi-line string literals, allowing developers to write formatted text and JSON-like content more naturally.

---

### JVM and Garbage Collection Enhancements

- **JEP 350: Dynamic CDS Archives**

  - Improved application startup and memory efficiency by allowing the dynamic archiving of classes at runtime.
- **JEP 351: ZGC: Uncommit Unused Memory**

  - Enhanced the **Z Garbage Collector** by allowing it to return unused heap memory to the operating system.

---

### Core Library and API Updates

- **JEP 353: Reimplement the Legacy Socket API**
  - Replaced the underlying implementation of the legacy `java.net.Socket` and `java.net.ServerSocket` APIs with a more modern and maintainable implementation.
