+++
title = "Java cơ bản"
date = "2024-12-18"
tags = [
    "markdown",
    "text",
]
+++

Java cung cấp một nền tảng mạnh mẽ cho lập trình viên với các khái niệm cơ bản như biến và kiểu dữ liệu, toán tử, cấu trúc điều khiển, hàm, và mảng. Việc hiểu rõ và sử dụng thành thạo các khái niệm này sẽ giúp bạn phát triển các ứng dụng Java hiệu quả và dễ dàng hơn.

## Biến và Kiểu Dữ Liệu trong Java
### Biến
Biến là khu vực trong bộ nhớ dùng để lưu trữ giá trị. Mỗi biến có tên và kiểu dữ liệu xác định.
Ví dụ khai báo và khởi tạo biến:
```java
    int age = 25;           // Biến kiểu int, lưu trữ số nguyên
    double salary = 1500.50; // Biến kiểu double, lưu trữ số thực
    String name = "John";    // Biến kiểu String, lưu trữ chuỗi ký tự
```
### Kiểu Dữ Liệu trong Java
#### Kiểu Dữ Liệu Nguyên Thủy (Primitive Data Types): 
Các kiểu dữ liệu này được định nghĩa sẵn trong Java, chúng không phải là đối tượng và chiếm một vùng bộ nhớ cụ thể.

- int: Kiểu số nguyên 32-bit.
```java
    int a = 10;
```
- double: Kiểu số thực 64-bit, có độ chính xác cao.
```java
    double price = 99.99;
```
- float: Kiểu số thực 32-bit, ít chính xác hơn double.
```java
    float temperature = 23.5f; // "f" là bắt buộc để chỉ rõ kiểu float
```
- char: Kiểu ký tự 16-bit.
```java
    char grade = 'A';
```
- boolean: Kiểu giá trị logic với hai giá trị true hoặc false.
```java
    boolean isActive = true;
```
- byte: Kiểu số nguyên 8-bit.
```java
    byte b = 120;
```
- short: Kiểu số nguyên 16-bit.
```java
    short s = 30000;
```
- long: Kiểu số nguyên 64-bit, dùng cho giá trị lớn.
```java
    long distance = 5000000000L; // "L" là bắt buộc
```
#### Kiểu Dữ Liệu Tham Chiếu (Reference Data Types): 
Đây là các kiểu dữ liệu tham chiếu đến các đối tượng trong bộ nhớ. Các kiểu này bao gồm String, các lớp (class) tự định nghĩa, và mảng.
Ví dụ khai báo kiểu tham chiếu:
```java
    String name = "Alice";  // Kiểu tham chiếu, lưu trữ chuỗi
    int[] numbers = {1, 2, 3}; // Kiểu tham chiếu, mảng số nguyên
```
## Toán Tử trong Java
Toán tử trong Java được sử dụng để thực hiện các phép toán trên dữ liệu. Java có các loại toán tử sau:

### Toán Tử Số Học (Arithmetic Operators)
- +: Cộng
- -: Trừ
- *: Nhân
- /: Chia
- %: Lấy phần dư (modulo)
Ví dụ:
```java
    int a = 10;
    int b = 5;
    System.out.println(a + b); // 15
    System.out.println(a - b); // 5
    System.out.println(a * b); // 50
    System.out.println(a / b); // 2
    System.out.println(a % b); // 0
```
### Toán Tử So Sánh (Comparison Operators)
- "==": So sánh bằng
- "!=": So sánh khác
- "<": Nhỏ hơn
- ">": Lớn hơn
- "<=": Nhỏ hơn hoặc bằng
- ">=": Lớn hơn hoặc bằng
Ví dụ:
```java
    int a = 10;
    int b = 20;
    System.out.println(a == b); // false
    System.out.println(a != b); // true
    System.out.println(a < b);  // true
```
### Toán Tử Logic (Logical Operators)
- &&: Và (AND)
- ||: Hoặc (OR)
- !: Phủ định (NOT)
Ví dụ:
```java
    boolean a = true;
    boolean b = false;
    System.out.println(a && b); // false
    System.out.println(a || b); // true
    System.out.println(!a);     // false
```
## Cấu Trúc Điều Kiển trong Java
### Câu Lệnh If-Else
Câu lệnh if-else giúp kiểm tra điều kiện và thực hiện hành động dựa trên điều kiện đó.

Ví dụ:

```java
    int age = 20;
    if (age >= 18) {
        System.out.println("Người trưởng thành");
    } else {
        System.out.println("Người chưa trưởng thành");
    }
```
### Câu Lệnh Switch
Câu lệnh switch giúp kiểm tra một biến có giá trị khớp với một trong nhiều trường hợp.

Ví dụ:
```java
int day = 3;
switch (day) {
    case 1:
        System.out.println("Thứ Hai");
        break;
    case 2:
        System.out.println("Thứ Ba");
        break;
    case 3:
        System.out.println("Thứ Tư");
        break;
    default:
        System.out.println("Không hợp lệ");
}
```
### Vòng Lặp (Loops)
- For Loop: Dùng khi biết số lần lặp.

Ví dụ:
```java
    for (int i = 0; i < 5; i++) {
        System.out.println(i); // In ra 0, 1, 2, 3, 4
    }
```
- While Loop: Dùng khi không biết số lần lặp trước, tiếp tục lặp khi điều kiện đúng.

Ví dụ:
```java
    int i = 0;
    while (i < 5) {
        System.out.println(i); // In ra 0, 1, 2, 3, 4
        i++;
    }
```
- Do-While Loop: Đảm bảo ít nhất một lần lặp, kiểm tra điều kiện sau mỗi lần thực hiện.

Ví dụ:
```java
    int i = 0;
    do {
        System.out.println(i); // In ra 0, 1, 2, 3, 4
        i++;
    } while (i < 5);
```
## Hàm trong Java
### Định Nghĩa Hàm (Method)
Hàm (hoặc phương thức) trong Java là một khối mã mà bạn có thể gọi nhiều lần, giúp tái sử dụng mã và tổ chức chương trình tốt hơn.

Ví dụ: Định nghĩa một hàm tính tổng của hai số.
```java
    public static int sum(int a, int b) {
        return a + b;
    }
```
### Gọi Hàm
Để gọi hàm, bạn chỉ cần gọi tên hàm và truyền tham số vào nếu có.

Ví dụ:
```java
    public class Main {
        public static void main(String[] args) {
            int result = sum(10, 5); // Gọi hàm sum
            System.out.println(result); // In ra 15
        }
        
        public static int sum(int a, int b) {
            return a + b;
        }
    }
```
## Mảng trong Java
### Khai Báo và Khởi Tạo Mảng
Mảng là một cấu trúc dữ liệu lưu trữ nhiều giá trị cùng loại trong một biến duy nhất.

- Khai báo mảng:
```java
    int[] numbers = new int[5];  // Mảng số nguyên với 5 phần tử
```
- Khởi tạo mảng với giá trị:
```java
    int[] numbers = {1, 2, 3, 4, 5}; // Mảng với 5 phần tử
```
### Truy Cập và Sửa Đổi Phần Tử Mảng
Bạn có thể truy cập phần tử của mảng bằng cách sử dụng chỉ số (index) bắt đầu từ 0.

Ví dụ:
```java
    int[] numbers = {1, 2, 3, 4, 5};
    System.out.println(numbers[0]); // In ra 1
    numbers[2] = 10; // Thay đổi giá trị tại chỉ số 2 thành 10
    System.out.println(numbers[2]); // In ra 10
```