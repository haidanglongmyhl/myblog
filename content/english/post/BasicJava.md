+++
title = "Basic Java"
date = "2024-12-18"
tags = [
    "markdown",
    "text",
]
+++

Java provides a powerful platform for developers with fundamental concepts such as variables and data types, operators, control structures, functions, and arrays. Understanding and mastering these concepts will help you develop Java applications more effectively and easily.

## Variables and Data Types in Java

### Variables
A variable is a location in memory used to store a value. Each variable has a name and a specific data type.

Example of declaring and initializing variables:
```java
    int age = 25;           // int type variable, stores integer value
    double salary = 1500.50; // double type variable, stores floating-point value
    String name = "John";    // String type variable, stores a text value
```
## Data Types in Java

### Primitive Data Types
These are the predefined data types in Java. They are not objects and occupy a specific amount of memory.

- **int**: 32-bit integer type.
```java
    int a = 10;
```
- **double**: 64-bit floating-point type, with high precision.
```java
    double price = 99.99;
```
- **float**: 32-bit floating-point type, less precise than double.
```java
    float temperature = 23.5f; // "f" là bắt buộc để chỉ rõ kiểu float
```
- **char**: 16-bit character type.
```java
    char grade = 'A';
```
- **boolean**: A logical data type with two values: true or false.
```java
    boolean isActive = true;
```
- **byte**: 8-bit integer type.
```java
    byte b = 120;
```
- **short**: 16-bit integer type.
```java
    short s = 30000;
```
- **long**: 64-bit integer type, used for larger values..
```java
    long distance = 5000000000L; // "L" là bắt buộc
```
#### Reference Data Types:
These are data types that refer to objects in memory. They include `String`, custom-defined classes, and arrays.

Example of declaring reference types:
```java
    String name = "Alice";  // Reference type, stores a string
    int[] numbers = {1, 2, 3}; // Reference type, stores an array of integers
```
## Arithmetic Operators in Java

Arithmetic operators in Java are used to perform mathematical operations on data. Java provides the following arithmetic operators:

### Arithmetic Operators
- `+`: Addition
- `-`: Subtraction
- `*`: Multiplication
- `/`: Division
- `%`: Modulus (remainder)

Example:
```java
    int a = 10;
    int b = 5;
    System.out.println(a + b); // 15
    System.out.println(a - b); // 5
    System.out.println(a * b); // 50
    System.out.println(a / b); // 2
    System.out.println(a % b); // 0
```
## Comparison Operators in Java

Comparison operators in Java are used to compare two values. They return a boolean value (`true` or `false`).

### Comparison Operators
- `==`: Equal to
- `!=`: Not equal to
- `<`: Less than
- `>`: Greater than
- `<=`: Less than or equal to
- `>=`: Greater than or equal to

Example:
```java
    int a = 10;
    int b = 20;
    System.out.println(a == b); // false
    System.out.println(a != b); // true
    System.out.println(a < b);  // true
```
## Logical Operators in Java

Logical operators in Java are used to perform logical operations on boolean values.

### Logical Operators
- `&&`: AND (both conditions must be true)
- `||`: OR (at least one condition must be true)
- `!`: NOT (reverses the boolean value)

Example:
```java
    boolean a = true;
    boolean b = false;
    System.out.println(a && b); // false
    System.out.println(a || b); // true
    System.out.println(!a);     // false
```
## Control Structures in Java

### If-Else Statement

The `if-else` statement allows you to check a condition and perform actions based on that condition.

### Example:

```java
    int age = 20;
    if (age >= 18) {
        System.out.println("Adult");
    } else {
        System.out.println("Not an adult");
    }
```
### Switch Statement

The `switch` statement allows you to check if a variable matches one of several possible cases.

### Example:

```java
    int day = 3;
    switch (day) {
        case 1:
            System.out.println("Monday");
            break;
        case 2:
            System.out.println("Tuesday");
            break;
        case 3:
            System.out.println("Wednesday");
            break;
        default:
            System.out.println("Invalid day");
    }
```
### Loops

- **For Loop**: Used when you know the number of iterations.

### Example:

```java
    for (int i = 0; i < 5; i++) {
        System.out.println(i); // Prints 0, 1, 2, 3, 4
    }
```
- **While Loop**: Used when the number of iterations is unknown beforehand, and it continues as long as the condition is true.

### Example:

```java
    int i = 0;
    while (i < 5) {
        System.out.println(i); // Prints 0, 1, 2, 3, 4
        i++;
    }
```
- **Do-While Loop**: Ensures that the loop runs at least once, checking the condition after each execution.

### Example:

```java
    int i = 0;
    do {
        System.out.println(i); // Prints 0, 1, 2, 3, 4
        i++;
    } while (i < 5);
```
## Methods in Java
### Defining a Method
A method (or function) in Java is a block of code that you can call multiple times, which helps in reusing code and organizing your program better.

### Example: Defining a method to calculate the sum of two numbers.

```java
    public static int sum(int a, int b) {
        return a + b;
    }
```
### Calling a Method
To call a method, you simply invoke the method by its name and pass any necessary arguments.

### Example:
```java
    public class Main {
        public static void main(String[] args) {
            int result = sum(10, 5); // Call the sum method
            System.out.println(result); // Outputs 15
        }
        
        public static int sum(int a, int b) {
            return a + b;
        }
    }
```
## Arrays in Java
### Declaring and Initializing Arrays
An array is a data structure that stores multiple values of the same type in a single variable.

- Declaring an array:
```java
    int[] numbers = new int[5];   // An array of integers with 5 elements
```
- Initializing an Array
```java
    int[] numbers = {1, 2, 3, 4, 5};  // Initialize array with values
```
### Accessing and Modifying Array Elements
You can access array elements by using their index, which starts from 0.
Example:
```java
    int[] numbers = {1, 2, 3, 4, 5};
    System.out.println(numbers[0]); // Outputs 1
    numbers[2] = 10; // Change the value at index 2 to 10
    System.out.println(numbers[2]); // Outputs 10
```