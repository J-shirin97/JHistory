# JEP 371: Hidden Classes  

## Introduction  

**Hidden Classes**, introduced in Java 15 through JEP 371, are special types of classes that are designed to be used by frameworks and runtime-generated code. These classes are not discoverable through standard reflection APIs, ensuring that they are private to the defining class loader. Hidden classes enable frameworks to define and use classes dynamically without polluting the runtime's namespace.  

---

## Why Do We Need Hidden Classes?  

1. **Support for Dynamic Frameworks**:  
   - Frameworks like Spring, Hibernate, and dynamic proxies often generate classes at runtime. Hidden classes allow these frameworks to manage dynamically generated classes without exposing them to the broader runtime environment.  

2. **Avoid Namespace Pollution**:  
   - Dynamically created classes can clutter the class namespace, causing potential conflicts or unintended behaviors. Hidden classes solve this by ensuring that such classes are not visible outside their class loader.  

3. **Enhanced Performance**:  
   - Hidden classes are optimized for single-use or framework-specific use cases, reducing runtime overhead.  

4. **Better Security and Encapsulation**:  
   - Hidden classes cannot be accessed via reflection, improving the encapsulation of dynamically generated logic.  

---

## How We Managed Before Hidden Classes  

Before hidden classes, developers relied on existing mechanisms to define dynamic classes, such as:  

1. **`ClassLoader.defineClass`**:  
   - Dynamically defines classes but makes them discoverable through the class loader, leading to namespace pollution.  

2. **`Unsafe` API**:  
   - Low-level methods like `Unsafe.defineAnonymousClass` were used, which were not secure, supported, or standardized.  

3. **Code Generation Libraries**:  
   - Libraries like ASM, CGLIB, or Javassist were commonly used, but the generated classes were still visible through reflection.  

### Issues:  
- Dynamic classes could unintentionally conflict with existing classes.  
- Debugging and maintenance became challenging due to namespace pollution.  
- Security concerns arose because dynamically generated classes were discoverable.  

---

## What Are Hidden Classes?  

Hidden classes are dynamically defined classes that:  
1. Are not discoverable through standard reflection.  
2. Can be unloaded when no longer in use.  
3. Are intended to be used by frameworks and not accessible by application code.  

### Key Features:  
- **Private to Class Loader**: Only accessible within the same class loader.  
- **No Reflection Access**: Not visible through `Class.forName` or other reflection methods.  
- **Optimized for Single Use**: Designed for short-lived, framework-specific tasks.  

---

## Using Hidden Classes  

The `Lookup` API in `MethodHandles` is used to define and interact with hidden classes.  

### Example: Defining a Hidden Class  

```java
import java.lang.invoke.MethodHandles;
import java.lang.invoke.MethodHandles.Lookup;
import java.util.Base64;

public class HiddenClassExample {
    public static void main(String[] args) throws Throwable {
        String classData = "yv66vgAAADQAHAoABgARCgACABIKAAIACwcABAAFBwAIAAcBAAYHAAkABwAKBwALAAYBAAEBAAoAAAACAAEAAAACAAEACQAAAB0AAQABAAAABAABAAkABAAGAAsAAAAEAAEAAAABAAEADAABAAEAAAADAAEAAAABAAoAAAABAAEAAAADAAEAAwAAAAEAAQABAAAAAQAC";
        byte[] classBytes = Base64.getDecoder().decode(classData);

        Lookup lookup = MethodHandles.lookup();
        Class<?> hiddenClass = lookup.defineHiddenClass(classBytes, true).lookupClass();

        System.out.println("Hidden class: " + hiddenClass);
    }
}
```

Explanation:

-    MethodHandles.Lookup: Provides access to define hidden classes.
-    defineHiddenClass: Dynamically defines a class as hidden and returns its Class object.
-    Class Data: In this example, a precompiled class in Base64 format is used.

Real-Life Scenarios
1. Dynamic Proxy Frameworks

Hidden classes allow frameworks to create proxies dynamically without exposing them to the runtime.

```java
public interface Service {
    void execute();
}

public class ProxyExample {
    public static void main(String[] args) throws Throwable {
        MethodHandles.Lookup lookup = MethodHandles.lookup();
        byte[] proxyClassBytes = createProxyClassBytes(); // Assume a method to generate proxy class bytes

        Class<?> proxyClass = lookup.defineHiddenClass(proxyClassBytes, true).lookupClass();
        Service proxy = (Service) proxyClass.getConstructor().newInstance();
        proxy.execute();
    }
}
```

2. Bytecode Manipulation Libraries

Tools like ASM or Javassist can use hidden classes to create runtime-modifiable classes without polluting the namespace.

3. Framework-Specific Logic

Frameworks like Hibernate can generate classes for lazy loading or proxying that are inaccessible to the application.
Advantages of Hidden Classes

1)    Namespace Isolation:
        Prevents dynamic classes from interfering with application classes.

2)    Security:
        Ensures dynamically generated classes are encapsulated and not discoverable via reflection.

3)    Memory Efficiency:
        Hidden classes can be unloaded independently, optimizing memory usage.

4)    Standardized API:
        Provides a secure and consistent approach to defining dynamic classes, replacing unsafe alternatives.

Limitations

1)   Framework-Oriented:
        Hidden classes are primarily for framework and library developers, not general application use.

2)    Debugging:
        Since hidden classes are not discoverable, debugging issues related to them may require specialized tools.

3)    Complexity:
        Using MethodHandles.Lookup requires understanding the underlying mechanisms of class loading and bytecode.

## Conclusion

Hidden classes provide a robust and secure mechanism for dynamically defining classes in Java. By isolating such classes from the application's namespace, they address long-standing challenges faced by frameworks and libraries in managing dynamically generated code. Hidden classes improve security, maintainability, and performance while offering a standardized alternative to legacy approaches like Unsafe.