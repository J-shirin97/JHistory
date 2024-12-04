# JDK 9 - Key Features and Enhancements

## Introduction  
Released on September 21, 2017, JDK 9 introduced several significant updates to the Java platform. The release was highlighted by the **Java Platform Module System** (Project Jigsaw), which modularized the JDK for improved performance, maintainability, and security. Additionally, JDK 9 featured numerous updates to libraries, tools, and the JVM.

## Key Features  

### 1. Modularization (Project Jigsaw)  
- Introduced the **Java Platform Module System** (JSR 376).  
- Enabled modular applications and encapsulated code dependencies.  
- Added tools like `jdeps` for analyzing dependencies and `jmod` for creating modular JAR files.

### 2. JShell (Java Shell)  
- Added a **Read-Eval-Print Loop (REPL)** tool for interactive coding and prototyping.  

### 3. Compact Strings  
- Improved memory usage by storing strings more efficiently, reducing heap consumption.

### 4. Concurrency Updates  
- Introduced the `Flow` API under **Reactive Streams** (JSR 266), enabling asynchronous, non-blocking data processing.  

### 5. Milling Project Coin  
- Added language refinements:  
  - `@SafeVarargs` on private methods.  
  - Effectively-final variables in [try-with-resources](Try-With-Resources%20in%20Java.md).  
  - Private methods in interfaces.  
  - Diamond operator support for anonymous classes.  

### 6. Ahead-of-Time Compilation (AOT)  
- Introduced experimental **Ahead-of-Time Compilation** using GraalVM to improve startup performance.  

### 7. jlink - The Java Linker  
- Added a tool for creating custom runtime images containing only the required modules for an application.  

### 8. HiDPI Graphics  
- Enhanced support for High-DPI displays with better scaling and rendering.  

### 9. XML Catalogs  
- Added support for managing XML external resources like schemas and DTDs.

### 10. Removal of JavaDB  
- Removed **JavaDB** from the JDK, as it was rarely used and available as Apache Derby.

