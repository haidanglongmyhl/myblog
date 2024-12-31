---
title: Object-Oriented Programming (OOP)
date: 2024-12-19
math: true
---

Enhance your system design and implementation skills.

<!--more-->

Object-Oriented Programming (OOP) is a programming paradigm that uses objects and classes to organize code. The fundamental concepts of OOP include Class, Object, Inheritance, Polymorphism, Encapsulation, and Abstraction.

## Classes and Objects
- **Class**: A class is a blueprint used to create objects. It defines attributes (variables) and methods (functions) for the objects.
- **Object**: An object is a specific instance of a class. Each object has a state and behavior defined by its class.

Example:
```java
    // Define a Car class
    class Car {
        String color; // Attribute (variable)
        String model;
        
        // Methods (functions)
        void start() {
            System.out.println("Car started");
        }

        void stop() {
            System.out.println("Car stopped");
        }
    }

    public class Main {
        public static void main(String[] args) {
            // Create objects (instances) of the Car class
            Car car1 = new Car();
            car1.color = "Red";
            car1.model = "Toyota";
            car1.start(); // Call the start method on car1
            
            Car car2 = new Car();
            car2.color = "Blue";
            car2.model = "Honda";
            car2.stop(); // Call the stop method on car2
        }
    }
```
## Inheritance
- **Inheritance** is a mechanism that allows a subclass to inherit attributes and methods from a superclass.
- The subclass can inherit elements from the superclass and can also add or override behavior.

### Example:
```java
    // Superclass
    class Animal {
        void sound() {
            System.out.println("Animal makes a sound");
        }
    }

    // Subclass inheriting from the Animal class
    class Dog extends Animal {
        // Override the sound method from the superclass
        @Override
        void sound() {
            System.out.println("Dog barks");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Dog dog = new Dog();
            dog.sound();  // Outputs "Dog barks"
        }
    }
```
## Polymorphism
Polymorphism allows an object of a subclass to be treated as an object of the superclass.

Polymorphism can be achieved in two ways:
- **Overloading**: When multiple methods have the same name but different parameters.
- **Overriding**: When a subclass changes (overrides) a method already defined in the superclass.

### Example of Overloading:
```java
    class Calculator {
        // Method for addition with two parameters
        int add(int a, int b) {
            return a + b;
        }

        // Method for addition with three parameters (overloaded)
        int add(int a, int b, int c) {
            return a + b + c;
        }
    }

    public class Main {
        public static void main(String[] args) {
            Calculator calculator = new Calculator();
            System.out.println(calculator.add(5, 10));     // Outputs 15
            System.out.println(calculator.add(5, 10, 15)); // Outputs 30
        }
    }
```
### Example of Overriding:
```java
    class Animal {
        void sound() {
            System.out.println("Animal makes a sound");
        }
    }

    class Cat extends Animal {
        @Override
        void sound() {
            System.out.println("Cat meows");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Animal animal = new Animal();
            animal.sound();  // In ra "Animal makes a sound"
            
            Animal cat = new Cat();
            cat.sound();  // In ra "Cat meows"
        }
    }
```
## Encapsulation
Encapsulation is the concept of hiding the internal details of a class and only allowing access and modification through public methods (getters/setters). This helps protect data and control access.

Attributes are typically declared as `private`, and getter and setter methods are used to retrieve and modify their values.

### Example:
```java
    class Person {
        // Private attribute
        private String name;
        
        // Getter method
        public String getName() {
            return name;
        }
        
        // Setter method
        public void setName(String name) {
            this.name = name;
        }
    }

    public class Main {
        public static void main(String[] args) {
            Person person = new Person();
            person.setName("Alice"); // Calling the setter to change the value
            System.out.println(person.getName()); // Calling the getter to retrieve the value
        }
    }
```
### Abstraction
Abstraction is the concept of hiding the implementation details and exposing only the necessary methods. Java supports abstraction through abstract classes and interfaces.
- An abstract class can contain abstract methods (methods without a body) and implemented methods.

### Abstract Class Example:
```java
    // Abstract class
    abstract class Animal {
        abstract void sound(); // Abstract method (no body)
        
        void sleep() {
            System.out.println("Animal is sleeping");
        }
    }

    class Dog extends Animal {
        // Implementing the sound method from the superclass
        @Override
        void sound() {
            System.out.println("Dog barks");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Dog dog = new Dog();
            dog.sound();  // Outputs "Dog barks"
            dog.sleep();  // Outputs "Animal is sleeping"
        }
    }
```
### Interface
An interface is a collection of abstract methods that a class must implement.

### Interface Example:
```java
    interface Animal {
        void sound(); // Abstract method in the interface
    }

    class Dog implements Animal {
        @Override
        public void sound() {
            System.out.println("Dog barks");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Animal dog = new Dog();
            dog.sound();  // Outputs "Dog barks"
        }
    }       
```
### Static Keyword
The `static` keyword in Java is used to indicate that a method or variable belongs to the class itself rather than to instances of the class. This means you can access them without creating an object of the class.

### Example:
```java
    class MathUtils {
        static int square(int x) {
            return x * x;
        }
    }

    public class Main {
        public static void main(String[] args) {
            System.out.println(MathUtils.square(5)); // Outputs 25
        }
    }
```
### Final Keyword
The `final` keyword in Java can be applied to classes, methods, and variables, and it enforces immutability or prevents modification.

- **Final class**: A class that cannot be subclassed (inherited).
- **Final method**: A method that cannot be overridden by subclasses.
- **Final variable**: A variable whose value cannot be changed once it has been assigned.

### Example:
```java
    // Final class cannot be inherited
    final class Vehicle {
        void move() {
            System.out.println("Vehicle is moving");
        }
    }

    // The following code would cause a compile-time error:
    // class Car extends Vehicle {} // Error: Cannot inherit from final 'Vehicle'

    public class Main {
        public static void main(String[] args) {
            Vehicle vehicle = new Vehicle();
            vehicle.move(); // Outputs "Vehicle is moving"
        }
    }
```
### Interfaces and Abstract Classes – Comparison

#### Interface:
- Can only contain abstract methods (before Java 8), but starting from Java 8, interfaces can also have default methods (methods with implementation).
- Cannot contain instance variables, only constants (static final variables).
- A class can implement multiple interfaces.

#### Abstract Class:
- Can contain both abstract methods (without implementation) and methods with implementation.
- Can have instance variables (state).
- A class can only inherit from one abstract class (single inheritance).

### Example:

```java
    // Interface
    interface Animal {
        void sound();
    }

    // Abstract class
    abstract class AnimalAbstract {
        abstract void sound();

        void sleep() {
            System.out.println("Animal is sleeping");
        }
    }

    class Dog extends AnimalAbstract implements Animal {
        @Override
        void sound() {
            System.out.println("Dog barks");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Dog dog = new Dog();
            dog.sound();  // Outputs "Dog barks"
            dog.sleep();  // Outputs "Animal is sleeping"
        }
    }
```
### Interfaces and Abstract Classes – Comparison

#### Interface:
- Can only contain abstract methods (before Java 8), but starting from Java 8, interfaces can also have default methods (methods with implementation).
- Cannot contain instance variables, only constants (static final variables).
- A class can implement multiple interfaces.

#### Abstract Class:
- Can contain both abstract methods (without implementation) and methods with implementation.
- Can have instance variables (state).
- A class can only inherit from one abstract class (single inheritance).

### Example:

```java
    // Interface
    interface Animal {
        void sound();
    }

    // Abstract class
    abstract class AnimalAbstract {
        abstract void sound();

        void sleep() {
            System.out.println("Animal is sleeping");
        }
    }

    class Dog extends AnimalAbstract implements Animal {
        @Override
        void sound() {
            System.out.println("Dog barks");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Dog dog = new Dog();
            dog.sound();  // Outputs "Dog barks"
            dog.sleep();  // Outputs "Animal is sleeping"
        }
    }
```
## String Class

The `String` class in Java is used to work with character strings. One important feature of the `String` class is that strings are immutable, meaning once a string is created, its value cannot be changed. If you perform any operation that modifies the string, a new string object is created.

### Common Methods of the `String` Class:
- **length()**: Returns the length of the string.
- **charAt(int index)**: Returns the character at the specified index.
- **substring(int start, int end)**: Extracts a substring from the string from the start index to the end index.
- **contains(CharSequence seq)**: Checks if the string contains the specified sequence of characters.
- **equals(String other)**: Compares the string with another string for equality.

### Example:

```java
    public class Main {
        public static void main(String[] args) {
            String greeting = "Hello, World!";
            
            // Get the length of the string
            System.out.println("Length: " + greeting.length()); // Outputs 13

            // Get the character at index 7
            System.out.println("Character at index 7: " + greeting.charAt(7)); // Outputs 'W'

            // Get substring from index 7 to the end
            System.out.println("Substring: " + greeting.substring(7)); // Outputs "World!"

            // Check if the string contains "Hello"
            System.out.println("Contains 'Hello': " + greeting.contains("Hello")); // Outputs true

            // Compare the string with another string
            String anotherGreeting = "Hello, World!";
            System.out.println("Equals: " + greeting.equals(anotherGreeting)); // Outputs true
        }
    }
```
## ArrayList Class

The `ArrayList` class in Java is part of the `java.util` package and provides a way to store a dynamic list of elements. Unlike arrays, the size of an `ArrayList` can change dynamically during runtime.

### Common Methods of the `ArrayList` Class:
- **add(E e)**: Adds an element to the list.
- **get(int index)**: Retrieves the element at the specified index.
- **remove(int index)**: Removes the element at the specified index.
- **size()**: Returns the number of elements in the list.
- **contains(Object o)**: Checks if an element exists in the list.

### Example:

```java
    import java.util.ArrayList;

    public class Main {
        public static void main(String[] args) {
            // Create an ArrayList of integers
            ArrayList<Integer> numbers = new ArrayList<>();

            // Add elements to the ArrayList
            numbers.add(10);
            numbers.add(20);
            numbers.add(30);

            // Get the element at index 1
            System.out.println("Element at index 1: " + numbers.get(1)); // Outputs 20

            // Remove the element at index 2
            numbers.remove(2);  // Removes 30

            // Get the size of the ArrayList
            System.out.println("Size of the list: " + numbers.size()); // Outputs 2

            // Check if an element exists in the list
            System.out.println("Contains 10? " + numbers.contains(10)); // Outputs true
        }
    }
```
## HashMap Class

The `HashMap` class in Java is part of the `java.util` package and is a data structure that allows you to store data in key-value pairs. Each key in a `HashMap` is unique, and it maps to a value.

### Common Methods of the `HashMap` Class:
- **put(K key, V value)**: Adds a key-value pair to the `HashMap`.
- **get(Object key)**: Retrieves the value associated with the given key.
- **remove(Object key)**: Removes the key-value pair associated with the specified key.
- **containsKey(Object key)**: Checks if the `HashMap` contains the given key.
- **size()**: Returns the number of key-value pairs in the `HashMap`.

### Example:

```java
    import java.util.HashMap;

    public class Main {
        public static void main(String[] args) {
            // Create a HashMap with String as key and Integer as value
            HashMap<String, Integer> map = new HashMap<>();

            // Add key-value pairs to the HashMap
            map.put("Alice", 25);
            map.put("Bob", 30);
            map.put("Charlie", 35);

            // Get the value by key
            System.out.println("Alice's age: " + map.get("Alice")); // Outputs 25

            // Check if a key exists
            System.out.println("Contains key 'Bob'? " + map.containsKey("Bob")); // Outputs true

            // Remove key-value pair by key
            map.remove("Charlie");

            // Get the size of the HashMap
            System.out.println("Size of the map: " + map.size()); // Outputs 2
        }
    }
```
## Conclusion
Object-Oriented Programming (OOP) in Java is not only about the fundamental concepts like classes, objects, inheritance, polymorphism, and encapsulation but also includes advanced techniques and features that enhance flexibility, maintainability, and scalability of software systems. Concepts like Composition, Aggregation, Static, Final, Lambda Expressions, and Concurrency extend the power and applicability of OOP, allowing developers to create more efficient, scalable, and easily maintainable applications.