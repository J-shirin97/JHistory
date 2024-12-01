# Lambda Expressions in Java

## Introduction

Lambda Expressions were introduced in Java 8 (JSR 335) as part of Project Lambda. They represent a paradigm shift in the way Java handles functional programming and improve productivity by simplifying the code for tasks like iterating over collections, handling events, and executing callbacks.

A **lambda expression** is essentially an anonymous function—a block of code that can be passed around, executed later, or applied directly to data streams. This functionality simplifies coding, reduces boilerplate, and allows Java to compete more effectively with functional programming languages.

---

## Why Do We Need Lambda Expressions?

Before lambda expressions, achieving tasks like passing a block of code (behavior) to a method required using **anonymous inner classes**. This was verbose and often cluttered codebases. Common tasks, such as iterating over a list or filtering a collection, involved repetitive patterns that made the code lengthy and harder to read.

### Key Problems Solved by Lambda Expressions

1. **Reduction of Boilerplate Code**:Lambdas allow concise representation of behavior without defining entire classes or methods.
2. **Improved Readability**:Code becomes shorter and easier to understand, especially for functional-style operations like `map`, `filter`, and `reduce`.
3. **Streamlined Functional Programming**:
   Lambdas power the **Streams API**, enabling developers to process collections in a declarative manner.

---

## How We Managed Before Lambdas

### Approach: Using Anonymous Inner Classes

Before lambdas, developers relied on anonymous inner classes to define blocks of behavior for tasks like event handling, iteration, or passing logic to methods.

Example: Filtering a List of Strings Before Lambdas

```java
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> names = List.of("Alice", "Bob", "Charlie", "Anna");

        // Filter names starting with 'A' (Before Lambda)
        List<String> filtered = new ArrayList<>();
        for (String name : names) {
            if (name.startsWith("A")) {
                filtered.add(name);
            }
        }

        System.out.println(filtered); // Output: [Alice, Anna]
    }
}
```


This code works but involves a lot of boilerplate logic. With lambdas, this can be reduced dramatically.


## Lambda Expressions: A Better Way

A lambda expression has the following structure:

```java
(parameters) -> { body }
```

Syntax Breakdown

    Parameters: Define the input values for the lambda.
    Arrow Operator (->): Separates parameters from the body of the function.
    Body: Contains the logic to execute, which could be a single expression or a block of statements.

Example: Lambda Expression for Filtering
```java
List<String> filtered = names.stream()
                             .filter(name -> name.startsWith("A"))
                             .collect(Collectors.toList());

System.out.println(filtered); // Output: [Alice, Anna]
```

## Real-Life Scenarios

#### 1. Event Handling in GUIs

Lambda expressions simplify the process of handling user interactions like button clicks.

Before Lambda:

```java
button.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        System.out.println("Button clicked!");
    }
});
```

With Lambda:
```java
button.addActionListener(e -> System.out.println("Button clicked!"));
```

#### 2. Sorting with Custom Logic
```java
Collections.sort(names, new Comparator<String>() {
    @Override
    public int compare(String o1, String o2) {
        return o1.compareTo(o2);
    }
});
```

With Lambda:

```java
names.sort((o1, o2) -> o1.compareTo(o2));
```

#### 3. Parallel Data Processing

Using lambdas with streams makes parallel processing trivial.

Example: Processing Orders in Parallel


```java
List<Order> orders = getOrders();

// Calculate total revenue from completed orders
double totalRevenue = orders.parallelStream()
                            .filter(Order::isCompleted)
                            .mapToDouble(Order::getAmount)
                            .sum();

System.out.println("Total Revenue: " + totalRevenue);
```



## How to Use Lambda Expressions

#### 1. Single-Line Lambdas
If the body is a single expression, the braces and return keyword are optional.

```java
Consumer<String> printer = message -> System.out.println(message);
printer.accept("Hello, Lambda!"); // Output: Hello, Lambda!
```




#### 2. Multi-Line Lambdas
For more complex logic, enclose the body in braces {} and use explicit return statements if needed.

```java
Function<Integer, Integer> square = num -> {
    int result = num * num;
    return result;
};
System.out.println(square.apply(5)); // Output: 25
```



## Functional Interfaces

A lambda expression can only be used where a functional interface is expected. A functional interface has exactly one abstract method.

Example: Using Runnable as a Functional Interface
```java
Runnable task = () -> System.out.println("Running in a separate thread!");
new Thread(task).start();
```

## Advantages of Lambda Expressions

1.    Concise Code: Reduces verbosity and makes the code cleaner.
2.    Enhanced Productivity: Simplifies common programming tasks.
 3.   Powerful Stream Operations: Enables declarative processing of collections.
 4.   Improved Performance: Stream API operations can leverage parallelism.


## Conclusion

Lambda expressions revolutionized Java by introducing functional programming constructs. They reduce boilerplate code, make functional-style operations more intuitive, and unlock powerful features like the Streams API. By understanding how to use lambdas effectively, developers can write more efficient and expressive Java code.