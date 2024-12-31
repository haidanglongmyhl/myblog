+++
title = "Những lỗi thường gặp khi học Java và cách khắc phục"
date = "2024-12-22"
tags = [
    "markdown",
    "css",
    "html",
]
aliases = ["migrate-from-jekyl"]
+++

Khi học Java, người mới bắt đầu thường gặp một số lỗi phổ biến do chưa nắm vững kiến thức cơ bản hoặc chưa có nhiều kinh nghiệm thực hành. Dưới đây là các lỗi thường gặp cùng giải pháp chi tiết để khắc phục.

<!--more-->

## Không hiểu rõ khái niệm OOP (Lập trình hướng đối tượng)

Nguyên nhân:
- Người học chưa nắm rõ các nguyên tắc cơ bản của OOP, như encapsulation (đóng gói), inheritance (kế thừa), polymorphism (đa hình), và abstraction (trừu tượng).
- Lẫn lộn giữa khái niệm lớp (class) và đối tượng (object).
Ví dụ lỗi:
- Tạo một lớp mà không sử dụng tính đóng gói (encapsulation):
```java
  public class Student {
      public String name;
      public int age;
  }
```
Cách khắc phục:
- Tìm hiểu lý thuyết cơ bản về OOP: Đọc sách hoặc tài liệu hướng dẫn cụ thể về các nguyên tắc OOP.
- Thực hành: Tạo các lớp với thuộc tính (fields) và phương thức (methods) có phạm vi truy cập phù hợp. 
- Ví dụ:
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
- Tập trung hiểu mối quan hệ giữa các lớp: Tạo các ví dụ nhỏ như lớp cha-con, sử dụng kế thừa và đa hình.
## Không xử lý đúng NullPointerException

Nguyên nhân:
- Truy cập vào đối tượng chưa được khởi tạo hoặc giá trị null.
- Không kiểm tra null trước khi sử dụng.
- Ví dụ lỗi:
```java
  String name = null;
  System.out.println(name.length()); // Gây NullPointerException
```
Cách khắc phục:
- Kiểm tra null trước khi sử dụng:
```java
  if (name != null) {
      System.out.println(name.length());
  } else {
      System.out.println("Tên không được để trống.");
  }
```
Sử dụng các API an toàn:
- Sử dụng Optional (Java 8 trở lên) để tránh null:
```java
  Optional<String> name = Optional.ofNullable(null);
  System.out.println(name.orElse("Tên mặc định"));
```
- Tuân thủ nguyên tắc "không để null" khi có thể: Đặt giá trị mặc định hoặc sử dụng Constructor để khởi tạo đối tượng.
## Nhầm lẫn giữa kiểu nguyên thủy và lớp đối tượng

Nguyên nhân:
- Người học chưa phân biệt được các kiểu nguyên thủy (primitive types) như int, double với các lớp đối tượng (wrapper classes) như Integer, Double.
- Không hiểu quá trình autoboxing và unboxing (tự động chuyển đổi giữa kiểu nguyên thủy và đối tượng).
- Ví dụ lỗi:
```java
  Integer a = null;
  int b = a; // Gây lỗi NullPointerException do unboxing từ null
```
Cách khắc phục:
- Hiểu rõ sự khác biệt: Kiểu nguyên thủy: int, double, boolean... dùng để lưu trữ dữ liệu đơn giản, hiệu quả hơn. Lớp đối tượng: Integer, Double, Boolean... có thể lưu giá trị null và chứa các phương thức hỗ trợ (như Integer.parseInt).
- Cẩn thận với null khi dùng wrapper classes:
```java
  Integer a = null;
  if (a != null) {
      int b = a; // Chỉ thực hiện unboxing nếu giá trị không null
  }
```
- Tránh lạm dụng autoboxing/unboxing khi hiệu suất quan trọng.
## Không tối ưu hóa code (viết code lặp)
Nguyên nhân:
- Người học chưa làm quen với các cấu trúc lập trình tối ưu như vòng lặp, hàm, hoặc các phương thức trong Java Collections.
- Viết mã thủ công thay vì tận dụng các API có sẵn.
- Ví dụ lỗi:
```java
  System.out.println("1");
  System.out.println("2");
  System.out.println("3");
  System.out.println("4");
  System.out.println("5");
```
Cách khắc phục:
- Sử dụng vòng lặp:
```java
  for (int i = 1; i <= 5; i++) {
      System.out.println(i);
  }
```
- Tận dụng các phương thức có sẵn:
Ví dụ, sử dụng forEach với danh sách:
```java
  List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
  names.forEach(System.out::println);
```
- Sử dụng hàm để tái sử dụng mã:
Thay vì viết lặp lại logic, hãy đóng gói vào các phương thức.
```java
  public void printNumbers(int n) {
      for (int i = 1; i <= n; i++) {
          System.out.println(i);
      }
  }
```
## Các lỗi phổ biến khác
### Không tuân thủ quy tắc đặt tên:
Sử dụng tên biến hoặc phương thức không rõ ràng, gây khó hiểu.

Cách khắc phục:
- Tuân thủ quy tắc đặt tên theo camelCase cho biến và phương thức, PascalCase cho lớp.
- Đặt tên gợi ý chức năng, như: calculateSum thay vì cs.
### Không sử dụng thư viện Java Collections hiệu quả:

Ví dụ lỗi: Lựa chọn ArrayList trong khi bài toán yêu cầu truy xuất nhanh (nên dùng HashMap).

Cách khắc phục:
- Tìm hiểu cách sử dụng các cấu trúc dữ liệu như List, Set, Map, và lựa chọn phù hợp.
### Quên đóng tài nguyên:
Không đóng file, kết nối database sau khi sử dụng, gây rò rỉ tài nguyên.
Cách khắc phục: Sử dụng try-with-resources:
```java
  try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
      System.out.println(br.readLine());
  } catch (IOException e) {
      e.printStackTrace();
  }
```
## Tóm lại
- Hiểu rõ khái niệm OOP, cách xử lý null, và sự khác biệt giữa kiểu nguyên thủy và đối tượng.
- Sử dụng các cấu trúc lập trình và thư viện Java một cách hiệu quả.
- Thực hành thường xuyên và học từ các lỗi để cải thiện kỹ năng lập trình.






