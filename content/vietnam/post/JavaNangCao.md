+++
title = "Java nâng cao"
date = "2024-12-20"
tags = [
    "emoji",
]
+++

Dưới đây là phần chi tiết về các chủ đề nâng cao trong Java: Xử lý ngoại lệ (Exception Handling), Streams và Lambda expressions, và Multi-threading và Concurrent programming.

<!--more-->

## Xử lý ngoại lệ (Exception Handling)
Xử lý ngoại lệ trong Java cho phép chương trình tiếp tục chạy ngay cả khi xảy ra các lỗi không lường trước, tránh việc chương trình bị sập khi có lỗi xảy ra. Java cung cấp cơ chế để phát hiện và xử lý các lỗi (exceptions) thông qua các khối mã try-catch-finally.

### Các loại ngoại lệ trong Java:

Checked exceptions: Là các ngoại lệ mà bạn phải xử lý (thường là các ngoại lệ có thể dự đoán được)
- IOException: Xảy ra khi có lỗi trong quá trình nhập/xuất, ví dụ như đọc/ghi file.
- SQLException: Lỗi khi thực hiện các thao tác liên quan đến cơ sở dữ liệu.
- ClassNotFoundException: Xảy ra khi không tìm thấy lớp trong quá trình tải lớp.
- FileNotFoundException: Xảy ra khi không thể tìm thấy tệp tin khi mở.
- InterruptedException: Được ném ra khi một luồng (thread) bị gián đoạn.
- ParseException: Xảy ra khi có lỗi khi phân tích chuỗi, chẳng hạn khi sử dụng các lớp như SimpleDateFormat.

Unchecked exceptions: Là các ngoại lệ không bắt buộc phải xử lý (thường là các lỗi do lỗi logic trong chương trình).
- NullPointerException: Xảy ra khi cố gắng truy cập vào đối tượng là null.
- ArrayIndexOutOfBoundsException: Xảy ra khi chỉ số truy cập mảng không hợp lệ.
- ArithmeticException: Xảy ra khi thực hiện các phép toán không hợp lệ, ví dụ như chia cho 0.
- ClassCastException: Xảy ra khi thực hiện ép kiểu không hợp lệ.
- NumberFormatException: Xảy ra khi chuyển đổi chuỗi thành số mà chuỗi đó không hợp lệ.
- IllegalArgumentException: Xảy ra khi một đối số được truyền vào phương thức không hợp lệ.
- IllegalStateException: Xảy ra khi trạng thái hiện tại của đối tượng không hợp lệ.

Error: Ngoài các ngoại lệ, Java còn có khái niệm Error. Đây là các vấn đề nghiêm trọng liên quan đến hệ thống mà không thể khôi phục hoặc xử lý được.
- OutOfMemoryError: Khi hệ thống hết bộ nhớ.
- StackOverflowError: Khi ngăn xếp gọi hàm bị tràn.
- VirtualMachineError: Các lỗi liên quan đến JVM.

Cấu trúc của xử lý ngoại lệ:
```java 
  try {
      // Mã có thể gây ra ngoại lệ
  } catch (ExceptionType1 e1) {
      // Xử lý ngoại lệ loại ExceptionType1
  } catch (ExceptionType2 e2) {
      // Xử lý ngoại lệ loại ExceptionType2
  } finally {
      // Mã này sẽ luôn chạy dù có ngoại lệ hay không
  }
```
Ví Dụ về Exception Handling:
```java
  import java.io.File;
  import java.io.FileNotFoundException;
  import java.util.Scanner;

  public class Main {
      public static void main(String[] args) {
          try {
              // Mở một tệp không tồn tại
              File file = new File("nonexistent.txt");
              Scanner scanner = new Scanner(file); // Gây ra FileNotFoundException
              System.out.println("File opened successfully");
          } catch (FileNotFoundException e) {
              // Xử lý lỗi khi không tìm thấy tệp
              System.out.println("File not found: " + e.getMessage());
          } finally {
              System.out.println("This block will always execute");
          }
      }
  }
```
- finally: Khối mã finally sẽ luôn được thực thi sau khi xử lý ngoại lệ, dù có ngoại lệ hay không, thường dùng để giải phóng tài nguyên (ví dụ: đóng tệp).
Tạo Exception tùy chỉnh:
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
              System.out.println(e.getMessage()); // In ra "Age cannot be negative"
          }
      }
  }
```
## Streams và Lambda Expressions
Java 8 giới thiệu Streams và Lambda expressions, hai tính năng mạnh mẽ giúp viết mã ngắn gọn và hiệu quả hơn, đặc biệt là trong việc xử lý bộ sưu tập dữ liệu.

### Lambda Expressions:
Lambda expressions cho phép bạn viết các phương thức vô danh (anonymous methods) một cách ngắn gọn. Lambda thường được sử dụng để truyền các đối tượng hàm vào phương thức, đặc biệt hữu ích khi làm việc với các API như Collections hoặc Streams.

Cú pháp Lambda:
```java
  (parameters) -> expression
```
Ví Dụ:
```java
  public class Main {
      public static void main(String[] args) {
          // Lambda expression để in ra một chuỗi
          Runnable r = () -> System.out.println("Hello, World!");
          r.run();  // In ra "Hello, World!"
      }
  }
```
### Streams API:
Stream là một đối tượng đại diện cho một chuỗi các phần tử có thể xử lý theo cách tuần tự hoặc song song. Stream có thể được sử dụng để lọc, sắp xếp, map, giảm (reduce) dữ liệu, và giúp bạn thao tác với bộ sưu tập một cách rõ ràng và hiệu quả hơn.

Cấu trúc Stream:
```java
  stream.filter(condition).map(transformation).collect(Collectors.toList());
```
Ví Dụ về Streams:
```java
  import java.util.Arrays;
  import java.util.List;
  import java.util.stream.Collectors;

  public class Main {
      public static void main(String[] args) {
          List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);

          // Lọc các số chẵn và nhân đôi chúng
          List<Integer> result = numbers.stream()
              .filter(n -> n % 2 == 0)  // Lọc số chẵn
              .map(n -> n * 2)          // Nhân đôi số chẵn
              .collect(Collectors.toList());  // Thu thập kết quả vào List

          System.out.println(result); // In ra [4, 8, 12, 16]
      }
  }
```
Các phương thức chính trong Streams:
- filter(): Lọc các phần tử theo điều kiện.
- map(): Biến đổi các phần tử.
- collect(): Thu thập kết quả thành một cấu trúc dữ liệu.
- reduce(): Thực hiện phép toán tích lũy trên các phần tử.
- forEach(): Duyệt qua các phần tử trong Stream.
## Multi-threading và Concurrent Programming
Multi-threading (đa luồng) là khả năng chạy nhiều đoạn mã đồng thời trong một chương trình. Điều này giúp tận dụng tối đa tài nguyên phần cứng và cải thiện hiệu suất cho các tác vụ tốn nhiều thời gian. Concurrent programming (lập trình đồng thời) là một kỹ thuật liên quan đến việc đồng bộ hóa các luồng để tránh lỗi do truy cập tài nguyên chung.

### Thread:
Trong Java, bạn có thể tạo luồng bằng cách kế thừa lớp Thread hoặc triển khai giao diện Runnable.

Cách tạo luồng:
Kế thừa lớp Thread:
```java
  class MyThread extends Thread {
      public void run() {
          System.out.println("Thread is running");
      }
  }

  public class Main {
      public static void main(String[] args) {
          MyThread t = new MyThread();
          t.start();  // Bắt đầu luồng
      }
  }
```
Triển khai giao diện Runnable:
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
### Sử dụng Executor Service:
ExecutorService cung cấp một cách thức dễ dàng và mạnh mẽ để quản lý các luồng.
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

          executorService.shutdown(); // Đóng Executor
      }
  }
```
### Synchronization (Đồng bộ hóa):
Để tránh các vấn đề khi nhiều luồng cùng truy cập vào dữ liệu chia sẻ, bạn cần đồng bộ hóa mã nguồn. Điều này có thể được thực hiện bằng cách sử dụng từ khóa synchronized.
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

          // Tạo hai luồng thực hiện việc tăng giá trị của count
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

          System.out.println("Final count: " + counter.getCount()); // In ra 2000
      }
  }
```
- join(): Đảm bảo rằng chương trình chính (main thread) sẽ đợi cho đến khi các luồng con hoàn thành công việc trước khi tiếp tục.
### Deadlock (Khóa chết):
Một vấn đề phổ biến khi làm việc với đa luồng là deadlock, khi hai hoặc nhiều luồng đang đợi lẫn nhau để giải phóng tài nguyên, dẫn đến tình trạng không thể tiếp tục chương trình.

Ví Dụ về Deadlock:
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
Trong ví dụ trên, khi hai luồng gọi methodA() và methodB() đồng thời, chúng sẽ gặp tình trạng deadlock.

## Tóm tắt:
- Xử lý ngoại lệ trong Java giúp xử lý các lỗi không lường trước và đảm bảo chương trình tiếp tục chạy bình thường.
- Lambda expressions và Streams giúp bạn viết mã ngắn gọn và hiệu quả, đặc biệt khi làm việc với các bộ sưu tập dữ liệu.
- Multi-threading và Concurrent programming giúp tận dụng tối đa tài nguyên phần cứng và xử lý các tác vụ đồng thời, nhưng đòi hỏi phải xử lý các vấn đề như đồng bộ hóa và deadlock.
Các chủ đề này là rất quan trọng trong việc xây dựng các ứng dụng Java hiệu quả, mạnh mẽ và dễ bảo trì.
