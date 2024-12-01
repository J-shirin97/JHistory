
# JDK 5 (1.5) - Key Features and Enhancements

## Introduction

Released on September 30, 2004, JDK 5 was a landmark release for Java, introducing significant language features and library improvements that greatly enhanced the language's expressiveness and ease of use. Originally numbered 1.5, the version was rebranded to "5.0" to better reflect its maturity and stability. This version was developed under JSR 176 and marked the last official support for several older operating systems, including Windows 98 and Windows ME.

## Key Features

### Language Changes

- **Generics**

  - Introduced compile-time type safety for collections, eliminating most typecasting and ensuring stronger type checks (specified by JSR 14).
- **Metadata (Annotations)**

  - Allowed tagging of classes, methods, and fields with additional metadata for processing by tools and frameworks (specified by JSR 175).
- **Autoboxing/Unboxing**

  - Enabled automatic conversions between primitive types (e.g., `int`) and their wrapper classes (e.g., `Integer`) (specified by JSR 201).
- **Enumerations (`enum` Keyword)**

  - Added a typesafe, ordered list of constants. Eliminated the need for manually constructed typesafe enum patterns (specified by JSR 201).
- **Varargs (Variable-length Arguments)**

  - Simplified method declarations for handling a varying number of arguments using the `...` syntax.
- **Enhanced for-each Loop**

  - Simplified iteration over arrays and collections with a new for-each syntax (specified by JSR 201).
- **Static Imports**

  - Allowed direct access to static members of a class without qualifying with the class name.
- **Improved Multi-threading Semantics**

  - Introduced a revised memory model to improve the clarity, effectiveness, and performance of multithreaded Java programs.

### Library Improvements

- **Automatic Stub Generation for RMI Objects**

  - Simplified development of distributed applications by automating stub creation for RMI objects.
- **Swing Enhancements**

  - Introduced the "Synth" skinnable look and feel for custom GUI themes.
- **Concurrency Utilities**

  - Added the `java.util.concurrent` package, providing high-performance threading and synchronization tools.
- **`Scanner` Class**

  - Introduced for easier parsing of input from various sources such as files and user input.
- **Other Improvements**

  - Integrated support for skinnable GUIs, improved network APIs, and additional cryptography extensions.

---
