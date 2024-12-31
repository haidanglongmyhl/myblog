+++
title = "Common Mistakes When Learning Java and How to Fix Them"
date = "2024-12-22"
tags = [
    "markdown",
    "css",
    "html",
]
aliases = ["migrate-from-jekyl"]
+++

When learning Java, beginners often encounter common mistakes due to a lack of understanding of basic concepts or insufficient practical experience. Below are some of the most frequent mistakes and detailed solutions to fix them.

<!--more-->

## Not Understanding the Concepts of OOP (Object-Oriented Programming)

Cause:
- Learners are not clear about the basic principles of OOP, such as encapsulation, inheritance, polymorphism, and abstraction.
- Confusing the concepts of class and object.
Example of Mistake:
- Creating a class without using encapsulation:
```java
  public class Student {
      public String name;
      public int age;
  }
```
Solution:
- Study the basic theory of OOP: Read books or documentation specifically about OOP principles.
- Practice: Create classes with appropriately scoped attributes (fields) and methods.
- Example:
```java
  public class Student {
      private String name;
      private int age;

      public String getName() {
          return name;
      }

      public void setName(String name) {
          this.name = name;
      }

      public int getAge() {
          return age;
      }

      public void setAge(int age) {
          this.age = age;
      }
  }
```
- Focus on understanding the relationships between classes: Create small examples using inheritance and polymorphism.
## Incorrect Handling of NullPointerException

Cause:
- Accessing an object that has not been initialized or is null.
- Not checking for null before usage.
Example of Mistake:
```java
  String name = null;
  System.out.println(name.length()); //Causes NullPointerException
```
Solution:
- Check for null before usage:
```java
  if (name != null) {
      System.out.println(name.length());
  } else {
      System.out.println("Name cannot be null.");
  }
```
Use safer APIs:
- Use Optional (Java 8 and later) to avoid null:
```java
  Optional<String> name = Optional.ofNullable(null);
  System.out.println(name.orElse("Default name"));
```
- Follow the "never null" principle when possible: Provide default values or initialize objects using constructors.
## Confusion Between Primitive Types and Wrapper Classes

Cause:
- Learners have trouble distinguishing between primitive types (int, double) and wrapper classes (Integer, Double).
- Not understanding the process of autoboxing and unboxing (automatic conversion between primitive types and objects).

Example of Mistake:
```java
  Integer a = null;
  int b = a; // Causes NullPointerException due to unboxing from null
```
Solution:
- Understand the difference: Primitive types (int, double, boolean, etc.) are used to store simple data more efficiently. Wrapper classes (Integer, Double, Boolean, etc.) can hold null values and provide supporting methods (like Integer.parseInt).
- Be cautious with null when using wrapper classes:
```java
  Integer a = null;
  if (a != null) {
      int b = a; // Only unbox if the value is not null
  }
```
- Avoid overusing autoboxing/unboxing when performance is important.
## Not Optimizing Code (Writing Repetitive Code)
Cause:
- Learners are not familiar with optimal programming structures like loops, functions, or Java Collections methods.
- Writing code manually instead of utilizing available APIs.
- Example of Mistake:
```java
  System.out.println("1");
  System.out.println("2");
  System.out.println("3");
  System.out.println("4");
  System.out.println("5");
```
Solution:
- Use loops:
```java
  for (int i = 1; i <= 5; i++) {
      System.out.println(i);
  }
```
- Use available methods: Example, using forEach with a list:
```java
  List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
  names.forEach(System.out::println);
```
- Use functions to reuse code: Instead of repeating logic, encapsulate it in methods:
```java
  public void printNumbers(int n) {
      for (int i = 1; i <= n; i++) {
          System.out.println(i);
      }
  }
```
## Other Common Mistakes
### Not Following Naming Conventions:
Using unclear variable or method names that cause confusion.

Solution:
- Follow naming conventions: Use camelCase for variables and methods, PascalCase for classes.
- Choose meaningful names, like calculateSum instead of cs.
### KNot Using Java Collections Libraries Effectively:

Example of mistake: Choosing ArrayList when the task requires fast access (use HashMap instead).

Solution:
- Learn how to use data structures like List, Set, Map, and choose the right one for the task.
### Forgetting to Close Resources:
Not closing files, database connections after use, causing resource leaks.

Solution:
- Use try-with-resources:
```java
  try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
      System.out.println(br.readLine());
  } catch (IOException e) {
      e.printStackTrace();
  }
```
## Conclusion
- Understand the concepts of OOP, how to handle null, and the difference between primitive types and objects.
- Use programming structures and Java libraries effectively.
- Practice regularly and learn from mistakes to improve programming skills.






