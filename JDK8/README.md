
# JDK 8 - Key Features and Enhancements

## Introduction

Released on March 18, 2014, JDK 8 introduced groundbreaking changes to the Java programming language and its standard libraries. This release focused on productivity, functional programming capabilities, and developer convenience. Many features deferred from Java 7 were included, making JDK 8 a transformative update.

The features in Java 8 were developed under JDK Enhancement Proposals (JEPs), introducing long-awaited enhancements like lambda expressions, a new Date and Time API, and functional-style programming on collections.

## Key Features

### Language Features

- **[Lambda Expressions](./Lambda%20Expressions.md) (JSR 335, JEP 126)**

  - Introduced concise syntax for defining anonymous functions.
  - Enabled functional programming with stream operations like `map`, `filter`, and `reduce`.
  - Simplified iteration and processing of collections.
- **Default Methods**

  - Allowed adding methods to interfaces without breaking existing implementations.
  - Facilitated API evolution and multiple inheritance of behavior.
- **Type Annotations (JEP 104)**

  - Supported annotations on any use of a type, improving integration with frameworks like dependency injection and validation tools.
- **Repeating Annotations (JEP 120)**

  - Allowed multiple annotations of the same type on a single program element.

### Core Libraries Enhancements

- **Streams API**

  - Provided a powerful new way to process sequences of elements from collections or other data sources.
  - Supported functional-style operations such as filtering, mapping, and reducing.
- **Date and Time API (JEP 150)**

  - Introduced a new `java.time` package for handling dates, times, durations, and intervals.
  - Replaced the confusing `java.util.Date` and `java.util.Calendar` with a modern, thread-safe API.
- **Unsigned Integer Arithmetic**

  - Added utility methods for unsigned arithmetic operations to the `Integer` and `Long` classes.
- **JavaFX Enhancements (JEP 153)**

  - Enabled direct launching of JavaFX application JARs without a separate launcher.

### JVM and Runtime Improvements

- **Project Nashorn (JEP 174)**

  - Introduced a high-performance JavaScript runtime for embedding JavaScript within Java applications.
- **Statically-Linked JNI Libraries (JEP 178)**

  - Enabled native libraries to be statically linked with the Java runtime.
- **Permanent Generation Removal (JEP 122)**

  - Removed the "PermGen" space in the JVM, simplifying memory management.

### Platform and Deployment Notes

- **Windows XP Compatibility**

  - Officially unsupported, but JDK 8 Update 25 and earlier versions could still run on Windows XP.
  - The last version of JDK 8 that could run on XP was Update 251.
- **JavaFX Integration**

  - Continued promotion of JavaFX as the primary GUI toolkit, replacing Swing for new applications.
- **Long-term Support for Personal Users**

  - Oracle committed to providing public updates of Java SE 8 indefinitely for personal users.

---
