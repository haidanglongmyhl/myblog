---
title: Hướng Đối Tượng (OOP) 
date: 2024-12-19
math: true
---

Nâng cao kỹ năng thiết kế và xây dựng hệ thống.

<!--more-->


Lập trình hướng đối tượng (OOP - Object-Oriented Programming) là một phương pháp lập trình sử dụng đối tượng và lớp để tổ chức mã nguồn. Các khái niệm cơ bản của OOP bao gồm Lớp (Class), Đối tượng (Object), Kế thừa (Inheritance), Đa hình (Polymorphism), Đóng gói (Encapsulation) và Trừu tượng (Abstraction).

## Lớp (Class) và Đối Tượng (Object)
- Lớp (Class): Lớp là một khuôn mẫu (template) dùng để tạo ra đối tượng. Nó định nghĩa các thuộc tính (biến) và phương thức (hàm) cho đối tượng.
- Đối tượng (Object): Đối tượng là thể hiện cụ thể của một lớp. Mỗi đối tượng có trạng thái và hành vi được định nghĩa bởi lớp của nó.
Ví Dụ:
```java
    // Định nghĩa lớp Car
    class Car {
        String color; // Thuộc tính (biến)
        String model;
        
        // Phương thức (hàm)
        void start() {
            System.out.println("Car started");
        }

        void stop() {
            System.out.println("Car stopped");
        }
    }

    public class Main {
        public static void main(String[] args) {
            // Tạo đối tượng (instantiation) từ lớp Car
            Car car1 = new Car();
            car1.color = "Red";
            car1.model = "Toyota";
            car1.start(); // Gọi phương thức start của đối tượng car1
            
            Car car2 = new Car();
            car2.color = "Blue";
            car2.model = "Honda";
            car2.stop(); // Gọi phương thức stop của đối tượng car2
        }
    }
```
## Kế Thừa (Inheritance)
- Kế thừa là một cơ chế cho phép một lớp con (subclass) kế thừa các thuộc tính và phương thức từ lớp cha (superclass).
- Lớp con có thể kế thừa các thành phần của lớp cha, và có thể bổ sung hoặc thay đổi hành vi (override).
Ví Dụ:
```java
    // Lớp cha (superclass)
    class Animal {
        void sound() {
            System.out.println("Animal makes a sound");
        }
    }

    // Lớp con (subclass) kế thừa từ lớp Animal
    class Dog extends Animal {
        // Override phương thức sound của lớp cha
        @Override
        void sound() {
            System.out.println("Dog barks");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Dog dog = new Dog();
            dog.sound();  // In ra "Dog barks"
        }
    }
```
## Đa Hình (Polymorphism)
Đa hình cho phép đối tượng của một lớp con có thể được xử lý như đối tượng của lớp cha.

Đa hình có thể được thực hiện theo hai cách:
- Overloading (Nạp chồng): Khi nhiều phương thức có cùng tên nhưng khác tham số.
- Overriding (Ghi đè): Khi lớp con thay đổi (override) phương thức đã có trong lớp cha.
Ví Dụ về Overloading (Nạp Chồng):
```java
    class Calculator {
        // Phương thức cộng với hai tham số
        int add(int a, int b) {
            return a + b;
        }

        // Phương thức cộng với ba tham số (nạp chồng)
        int add(int a, int b, int c) {
            return a + b + c;
        }
    }

    public class Main {
        public static void main(String[] args) {
            Calculator calculator = new Calculator();
            System.out.println(calculator.add(5, 10));     // In ra 15
            System.out.println(calculator.add(5, 10, 15)); // In ra 30
        }
    }
```
Ví Dụ về Overriding (Ghi Đè):
```java
    class Animal {
        void sound() {
            System.out.println("Animal makes a sound");
        }
    }

    class Cat extends Animal {
        // Override phương thức sound của lớp cha
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
## Đóng Gói (Encapsulation)
- Đóng gói là việc ẩn thông tin chi tiết của một lớp, chỉ cho phép truy cập và sửa đổi thông qua các phương thức công khai (getter/setter). Điều này giúp bảo vệ dữ liệu và kiểm soát truy cập.
- Các thuộc tính thường được khai báo là private, và các phương thức getter và setter được sử dụng để truy xuất và thay đổi giá trị.
Ví Dụ:
```java
    class Person {
        // Thuộc tính private
        private String name;
        
        // Getter
        public String getName() {
            return name;
        }
        
        // Setter
        public void setName(String name) {
            this.name = name;
        }
    }

    public class Main {
        public static void main(String[] args) {
            Person person = new Person();
            person.setName("Alice"); // Gọi setter để thay đổi giá trị
            System.out.println(person.getName()); // Gọi getter để lấy giá trị
        }
    }
```
### Trừu Tượng (Abstraction)
- Trừu tượng là việc ẩn đi chi tiết cài đặt và chỉ để lộ ra các phương thức cần thiết. Java hỗ trợ trừu tượng thông qua lớp trừu tượng (abstract class) và giao diện (interface).
- Một lớp trừu tượng có thể chứa các phương thức trừu tượng (không có thân phương thức) và phương thức đã cài đặt.
### Lớp Trừu Tượng:
```java
    // Lớp trừu tượng
    abstract class Animal {
        abstract void sound(); // Phương thức trừu tượng (không có thân)
        
        void sleep() {
            System.out.println("Animal is sleeping");
        }
    }

    class Dog extends Animal {
        // Cài đặt phương thức sound của lớp cha
        @Override
        void sound() {
            System.out.println("Dog barks");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Dog dog = new Dog();
            dog.sound();  // In ra "Dog barks"
            dog.sleep();  // In ra "Animal is sleeping"
        }
    }
```
### Giao Diện (Interface):
Giao diện (interface) là một tập hợp các phương thức trừu tượng mà một lớp phải cài đặt.
```java
    interface Animal {
        void sound(); // Phương thức trừu tượng trong giao diện
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
            dog.sound();  // In ra "Dog barks"
        }
    }       
```
## Static Keyword
Static là một từ khóa trong Java để chỉ ra rằng một phương thức hoặc thuộc tính không phụ thuộc vào đối tượng cụ thể mà thay vào đó là thuộc về lớp. Điều này có nghĩa là bạn có thể truy cập chúng mà không cần phải tạo đối tượng của lớp.
Ví Dụ:
```java
    class MathUtils {
        static int square(int x) {
            return x * x;
        }
    }

    public class Main {
        public static void main(String[] args) {
            System.out.println(MathUtils.square(5)); // In ra 25
        }
    }
```
## Final Keyword
Final là một từ khóa trong Java có thể được áp dụng cho các lớp, phương thức và biến.
- Final class: Lớp không thể kế thừa.
- Final method: Phương thức không thể bị ghi đè (override).
- Final variable: Biến không thể thay đổi giá trị sau khi được gán lần đầu.
Ví Dụ:
```java
    // Lớp final không thể kế thừa
    final class Vehicle {
        void move() {
            System.out.println("Vehicle is moving");
        }
    }

    // Lớp con không thể kế thừa từ lớp final Vehicle
    // class Car extends Vehicle {} // Sẽ gây lỗi biên dịch

    public class Main {
        public static void main(String[] args) {
            Vehicle vehicle = new Vehicle();
            vehicle.move(); // In ra "Vehicle is moving"
        }
    }
```
## Interfaces and Abstract Classes – So Sánh
Interface:
- Chỉ có thể chứa các phương thức trừu tượng (trước Java 8), nhưng từ Java 8 trở đi, các phương thức có thể có cài đặt mặc định (default methods).
- Không thể chứa trạng thái (biến) mà chỉ chứa các hằng số (constants).
- Một lớp có thể implements nhiều interfaces.

Abstract Class:
- Có thể có cả phương thức trừu tượng và phương thức có cài đặt.
- Có thể có trạng thái (biến).
- Một lớp chỉ có thể kế thừa một lớp abstract.
Ví Dụ:
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
            dog.sound();  // In ra "Dog barks"
            dog.sleep();  // In ra "Animal is sleeping"
        }
    }
```
## Access Modifiers (Modifier truy cập)
Java có các access modifiers giúp kiểm soát quyền truy cập vào các lớp, phương thức, và thuộc tính. Các access modifiers cơ bản là:
- Public: Có thể truy cập từ bất kỳ đâu.
- Private: Chỉ có thể truy cập trong lớp.
- Protected: Có thể truy cập trong cùng một package hoặc các lớp con.
- Default (package-private): Nếu không chỉ định, mặc định là package-private, có thể truy cập trong cùng package.
Ví Dụ:
```java 
class MyClass {
    public int publicVar;
    private int privateVar;

    public void publicMethod() {
        System.out.println("This is a public method");
    }

    private void privateMethod() {
        System.out.println("This is a private method");
    }
}

public class Main {
    public static void main(String[] args) {
        MyClass obj = new MyClass();
        obj.publicVar = 5;  // Được phép vì public
        // obj.privateVar = 10; // Lỗi: privateVar là private

        obj.publicMethod();  // Được phép vì public
        // obj.privateMethod(); // Lỗi: privateMethod là private
    }
}
```
## Lớp String
Lớp String trong Java được sử dụng để làm việc với chuỗi ký tự. Một trong những đặc điểm quan trọng của lớp String là chuỗi trong Java là bất biến (immutable), có nghĩa là một khi chuỗi được tạo ra, giá trị của nó không thể thay đổi. Nếu bạn thực hiện một thao tác thay đổi chuỗi, một đối tượng chuỗi mới sẽ được tạo ra.

Các phương thức phổ biến của lớp String:
- length(): Trả về độ dài của chuỗi.
- charAt(int index): Lấy ký tự tại vị trí chỉ số.
- substring(int start, int end): Cắt chuỗi từ chỉ số bắt đầu đến chỉ số kết thúc.
- contains(CharSequence seq): Kiểm tra chuỗi có chứa chuỗi con hay không.
- equals(String other): So sánh chuỗi với chuỗi khác.
Ví Dụ:
```java
    public class Main {
        public static void main(String[] args) {
            String greeting = "Hello, World!";
            
            // Lấy độ dài chuỗi
            System.out.println("Length: " + greeting.length()); // In ra 13

            // Lấy ký tự tại vị trí chỉ số 7
            System.out.println("Character at index 7: " + greeting.charAt(7)); // In ra 'W'

            // Cắt chuỗi từ chỉ số 7 đến hết
            System.out.println("Substring: " + greeting.substring(7)); // In ra "World!"

            // Kiểm tra chuỗi có chứa "Hello" hay không
            System.out.println("Contains 'Hello': " + greeting.contains("Hello")); // In ra true

            // So sánh chuỗi
            String anotherGreeting = "Hello, World!";
            System.out.println("Equals: " + greeting.equals(anotherGreeting)); // In ra true
        }
    }
```
## Lớp ArrayList
Lớp ArrayList trong Java là một lớp trong gói java.util cung cấp khả năng lưu trữ một danh sách động các phần tử. Khác với mảng, kích thước của ArrayList có thể thay đổi linh hoạt trong quá trình thực thi chương trình.

Các phương thức phổ biến của lớp ArrayList:
- add(E e): Thêm phần tử vào danh sách.
- get(int index): Lấy phần tử tại chỉ số.
- remove(int index): Xóa phần tử tại chỉ số.
- size(): Lấy số lượng phần tử trong danh sách.
- contains(Object o): Kiểm tra xem phần tử có tồn tại trong danh sách không.
Ví Dụ:
```java
    import java.util.ArrayList;

    public class Main {
        public static void main(String[] args) {
            // Tạo một ArrayList chứa các số nguyên
            ArrayList<Integer> numbers = new ArrayList<>();

            // Thêm phần tử vào ArrayList
            numbers.add(10);
            numbers.add(20);
            numbers.add(30);

            // Lấy phần tử tại chỉ số 1
            System.out.println("Element at index 1: " + numbers.get(1)); // In ra 20

            // Xóa phần tử tại chỉ số 2
            numbers.remove(2);  // Xóa 30

            // Lấy kích thước của ArrayList
            System.out.println("Size of the list: " + numbers.size()); // In ra 2

            // Kiểm tra sự tồn tại của một phần tử
            System.out.println("Contains 10? " + numbers.contains(10)); // In ra true
        }
    }
```
## Lớp HashMap
Lớp HashMap trong Java là một cấu trúc dữ liệu trong gói java.util cho phép lưu trữ dữ liệu theo dạng cặp khóa-giá trị (key-value). Mỗi khóa trong HashMap là duy nhất và có thể ánh xạ đến một giá trị bất kỳ.

Các phương thức phổ biến của lớp HashMap:
- put(K key, V value): Thêm cặp khóa-giá trị vào HashMap.
- get(Object key): Lấy giá trị theo khóa.
- remove(Object key): Xóa cặp khóa-giá trị theo khóa.
- containsKey(Object key): Kiểm tra xem có tồn tại khóa trong HashMap không.
- size(): Lấy số lượng cặp khóa-giá trị trong HashMap.
Ví Dụ:
```java
    import java.util.HashMap;

    public class Main {
        public static void main(String[] args) {
            // Tạo một HashMap với khóa là String và giá trị là Integer
            HashMap<String, Integer> map = new HashMap<>();

            // Thêm cặp khóa-giá trị vào HashMap
            map.put("Alice", 25);
            map.put("Bob", 30);
            map.put("Charlie", 35);

            // Lấy giá trị theo khóa
            System.out.println("Alice's age: " + map.get("Alice")); // In ra 25

            // Kiểm tra xem khóa có tồn tại không
            System.out.println("Contains key 'Bob'? " + map.containsKey("Bob")); // In ra true

            // Xóa cặp khóa-giá trị theo khóa
            map.remove("Charlie");

            // Lấy số lượng cặp khóa-giá trị trong HashMap
            System.out.println("Size of the map: " + map.size()); // In ra 2
        }
    }
```
## Kết luận
OOP không chỉ bao gồm các khái niệm cơ bản mà còn có những kỹ thuật và tính năng nâng cao giúp tăng cường tính linh hoạt và khả năng bảo trì của phần mềm. Những khái niệm như Composition, Aggregation, Static, Final, Lambda Expressions, và Concurrency mở rộng khả năng và ứng dụng của OOP trong Java, giúp lập trình viên tạo ra các ứng dụng hiệu quả hơn và dễ mở rộng.