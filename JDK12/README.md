
# JDK 12 - Key Features and Enhancements

## Introduction

Released on March 19, 2019, JDK 12 brought significant updates to the Java platform, focusing on garbage collection improvements, new APIs, and language enhancements. Several features, such as Switch Expressions, were introduced as preview features, allowing developers to explore and provide feedback for future refinements.

---

## Key Features

### Language Features

- **JEP 325: [Switch Expressions](./Switch%20Expressions.md) (Preview)**
  - Introduced a new form of the `switch` statement, allowing it to be used as an expression. This enhancement improves readability and reduces boilerplate code.

---

### JVM and Garbage Collection Enhancements

- **JEP 189: Shenandoah Garbage Collector (Experimental)**

  - Introduced Shenandoah, a low-pause-time garbage collector designed for applications requiring predictable and short pause durations.
- **JEP 344: Abortable Mixed Collections for G1**

  - Enhanced the G1 Garbage Collector by making mixed garbage collection phases abortable to reduce pause times.
- **JEP 346: Promptly Return Unused Committed Memory from G1**

  - Allowed G1 to release unused heap memory back to the operating system more promptly, improving memory efficiency.

---

### Library and Tooling Improvements

- **JEP 230: Microbenchmark Suite**

  - Added a microbenchmarking framework based on the Java Microbenchmark Harness (JMH) to help developers measure and optimize code performance.
- **JEP 334: JVM Constants API**

  - Introduced a new API for modeling key class-file and runtime artifacts, simplifying interaction with constants in the JVM.
- **JEP 341: Default CDS Archives**

  - Improved startup time and memory usage by creating Class Data Sharing (CDS) archives during the JDK build, making CDS enabled by default.

---

### Platform and Build Updates

- **JEP 340: One AArch64 Port, Not Two**
  - Consolidated the two existing ARM64 (AArch64) ports into a single implementation to simplify maintenance and improve performance.
