+++
title = "Advanced Java"
date = "2024-12-20"
tags = [
    "emoji",
]
+++

Below is a detailed guide on advanced Java topics: Exception Handling, Streams and Lambda expressions, and Multi-threading and Concurrent programming.

<!--more-->

## Exception Handling
Exception handling in Java allows the program to continue running even when unexpected errors occur, preventing the program from crashing when an error happens. Java provides a mechanism to detect and handle errors (exceptions) through try-catch-finally blocks.

### Types of Exceptions in Java:

**Checked exceptions:** These are exceptions that must be handled (usually predictable exceptions).
- `IOException`: Occurs during input/output operations, such as reading/writing files.
- `SQLException`: Errors during database-related operations.
- `ClassNotFoundException`: Occurs when a class cannot be found during class loading.
- `FileNotFoundException`: Occurs when a file cannot be found when opened.
- `InterruptedException`: Thrown when a thread is interrupted.
- `ParseException`: Occurs when there's an error parsing a string, such as when using classes like `SimpleDateFormat`.

**Unchecked exceptions:** These are exceptions that do not have to be handled (usually errors due to logic issues in the program).
- `NullPointerException`: Occurs when trying to access an object that is null.
- `ArrayIndexOutOfBoundsException`: Occurs when an invalid array index is accessed.
- `ArithmeticException`: Occurs when performing invalid arithmetic operations, such as dividing by zero.
- `ClassCastException`: Occurs when performing an invalid cast.
- `NumberFormatException`: Occurs when a string cannot be converted into a number.
- `IllegalArgumentException`: Occurs when an invalid argument is passed to a method.
- `IllegalStateException`: Occurs when the current state of an object is invalid.

**Error:** In addition to exceptions, Java also has the concept of Errors. These are serious system-related issues that cannot be recovered from or handled.
- `OutOfMemoryError`: When the system runs out of memory.
- `StackOverflowError`: When the function call stack overflows.
- `VirtualMachineError`: Errors related to the JVM.

### Exception Handling Structure:
```java
  try {
      // Code that may throw an exception
  } catch (ExceptionType1 e1) {
      // Handle ExceptionType1
  } catch (ExceptionType2 e2) {
      // Handle ExceptionType2
  } finally {
      // This code will always run, regardless of whether an exception occurred or not
  }
```
### Example of Exception Handling:
```java
  import java.io.File;
  import java.io.FileNotFoundException;
  import java.util.Scanner;

  public class Main {
      public static void main(String[] args) {
          try {
              // Open a non-existent file
              File file = new File("nonexistent.txt");
              Scanner scanner = new Scanner(file); // Causes FileNotFoundException
              System.out.println("File opened successfully");
          } catch (FileNotFoundException e) {
              // Handle the error when the file is not found
              System.out.println("File not found: " + e.getMessage());
          } finally {
              System.out.println("This block will always execute");
          }
      }
  }
```
- finally: The last block of code will always be executed after the exception is handled, whether there is an exception or not, usually used to free up resources (e.g. closing a file).
Creating a custom exception:
```java
  class InvalidAgeException extends Exception {
      public InvalidAgeException(String message) {
          super(message);
      }
  }

  public class Main {
      public static void main(String[] args) {
          try {
              int age = -1;
              if (age < 0) {
                  throw new InvalidAgeException("Age cannot be negative");
              }
          } catch (InvalidAgeException e) {
              System.out.println(e.getMessage()); // Print ra "Age cannot be negative"
          }
      }
  }
```
## Streams and Lambda Expressions
Java 8 introduced Streams and Lambda expressions, two powerful features that help write more concise and efficient code, especially when working with data collections.

### Lambda Expressions:
Lambda expressions allow you to write anonymous methods (also known as anonymous functions) concisely. Lambdas are often used to pass function objects to methods, which is especially useful when working with APIs like Collections or Streams.

Lambda syntax:
```java
  (parameters) -> expression
```
Example:
```java
  public class Main {
      public static void main(String[] args) {
          Runnable r = () -> System.out.println("Hello, World!");
          r.run();  // Print "Hello, World!"
      }
  }
```
### Streams API:
A Stream is an object that represents a sequence of elements that can be processed sequentially or in parallel. Streams can be used to filter, sort, map, reduce data, and help you manipulate collections more clearly and efficiently.

Stream structure:
```java
  stream.filter(condition).map(transformation).collect(Collectors.toList());
```
Example for Streams:
```java
    import java.util.Arrays;
    import java.util.List;
    import java.util.stream.Collectors;

    public class Main {
        public static void main(String[] args) {
            List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);

            // Filter even numbers and double them
            List<Integer> result = numbers.stream()
                .filter(n -> n % 2 == 0)  // Filter even numbers
                .map(n -> n * 2)          // Double the even numbers
                .collect(Collectors.toList());  // Collect the result into a List

            System.out.println(result); // Outputs [4, 8, 12, 16]
        }
    }
```
Main Methods in Streams:
- **filter()**: Filters elements based on a condition.
- **map()**: Transforms elements.
- **collect()**: Collects results into a data structure.
- **reduce()**: Performs a cumulative operation on elements.
- **forEach()**: Iterates through elements in a Stream.

## Multi-threading and Concurrent Programming
Multi-threading is the ability to run multiple code segments simultaneously within a program. It helps maximize hardware resources and improves performance for time-consuming tasks. Concurrent programming is a technique related to synchronizing threads to avoid errors caused by shared resource access.

### Thread:
In Java, you can create threads by either extending the `Thread` class or implementing the `Runnable` interface.

Creating a thread by extending the `Thread` class:
```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t = new MyThread();
        t.start();  // Start the thread
    }
}
```
Implementing the Runnable Interface:
```java
  class MyRunnable implements Runnable {
      public void run() {
          System.out.println("Thread is running");
      }
  }

  public class Main {
      public static void main(String[] args) {
          MyRunnable runnable = new MyRunnable();
          Thread thread = new Thread(runnable);
          thread.start();  // Bắt đầu luồng
      }
  }
```
### Using ExecutorService:
ExecutorService provides an easy and powerful way to manage threads.
```java
    import java.util.concurrent.ExecutorService;
    import java.util.concurrent.Executors;

    public class Main {
        public static void main(String[] args) {
            ExecutorService executorService = Executors.newFixedThreadPool(2);

            executorService.submit(() -> {
                System.out.println("Task 1 is running");
            });
            executorService.submit(() -> {
                System.out.println("Task 2 is running");
            });

            executorService.shutdown(); // Shut down the Executor
        }
    }
```
### Synchronization:
To avoid issues when multiple threads access shared data, you need to synchronize the code. This can be done using the `synchronized` keyword.

```java
class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;
    }

    public int getCount() {
        return count;
    }
}

public class Main {
    public static void main(String[] args) {
        Counter counter = new Counter();

        // Create two threads that increment the count value
        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                counter.increment();
            }
        });

        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                counter.increment();
            }
        });

        t1.start();
        t2.start();

        try {
            t1.join();
            t2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("Final count: " + counter.getCount()); // Prints 2000
    }
}
```
- join(): The `join()` method ensures that the main program (main thread) waits until the child threads complete their tasks before continuing.

### Deadlock:
A common issue when working with multithreading is deadlock, where two or more threads are waiting on each other to release resources, leading to a situation where the program cannot proceed.

Example of Deadlock:
```java
class A {
    synchronized void methodA(B b) {
        b.last();
    }

    synchronized void last() {}
}

class B {
    synchronized void methodB(A a) {
        a.last();
    }

    synchronized void last() {}
}

public class Main {
    public static void main(String[] args) {
        A a = new A();
        B b = new B();

        new Thread(() -> a.methodA(b)).start();
        new Thread(() -> b.methodB(a)).start();
    }
}
```
In the above example, when two threads call methodA() and methodB() simultaneously, they will get deadlocked.

## Summary:
- Exception handling in Java helps handle unexpected errors and ensures the program continues to run normally.
- Lambda expressions and Streams allow you to write concise and efficient code, especially when working with data collections.
- Multi-threading and Concurrent programming help maximize hardware resources and handle tasks concurrently, but require addressing issues like synchronization and deadlock

These topics are crucial in building efficient, robust, and maintainable Java applications.
