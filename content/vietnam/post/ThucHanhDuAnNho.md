+++
title = "Thực hành dự án nhỏ"
date = "2024-12-21"
+++

Dưới đây là hướng dẫn chi tiết để thực hiện hai dự án nhỏ bằng Java: Ứng dụng Quản lý Học sinh và Ứng dụng TODO List. Cả hai dự án này sẽ giúp bạn làm quen với các khái niệm cơ bản và nâng cao trong Java, bao gồm xử lý ngoại lệ, cấu trúc dữ liệu, lập trình đối tượng, và giao diện người dùng cơ bản.


## Ứng dụng Quản lý Học sinh
Ứng dụng này sẽ quản lý thông tin học sinh (tên, tuổi, lớp học, điểm số) và có các chức năng cơ bản như thêm, sửa, xóa và hiển thị danh sách học sinh.

Các lớp và đối tượng:
- Lớp Student: Lớp này sẽ chứa các thuộc tính của học sinh như tên, tuổi, lớp học, và điểm số.
- Lớp StudentManager: Quản lý các học sinh, bao gồm các phương thức thêm, sửa, xóa học sinh.
- Lớp Main: Lớp chính để chạy ứng dụng.
Bước 1: Tạo lớp Student
```java 
    public class Student {
        private String name;
        private int age;
        private String className;
        private double score;

        // Constructor
        public Student(String name, int age, String className, double score) {
            this.name = name;
            this.age = age;
            this.className = className;
            this.score = score;
        }

        // Getter và Setter
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

        public String getClassName() {
            return className;
        }

        public void setClassName(String className) {
            this.className = className;
        }

        public double getScore() {
            return score;
        }

        public void setScore(double score) {
            this.score = score;
        }

        @Override
        public String toString() {
            return "Student{name='" + name + "', age=" + age + ", class='" + className + "', score=" + score + "}";
        }
    }
```
Bước 2: Tạo lớp StudentManager để quản lý học sinh
```java
    import java.util.ArrayList;
    import java.util.List;

    public class StudentManager {
        private List<Student> students;

        public StudentManager() {
            this.students = new ArrayList<>();
        }

        // Thêm học sinh
        public void addStudent(Student student) {
            students.add(student);
        }

        // Hiển thị danh sách học sinh
        public void showStudents() {
            if (students.isEmpty()) {
                System.out.println("No students in the system.");
            } else {
                for (Student student : students) {
                    System.out.println(student);
                }
            }
        }

        // Xóa học sinh
        public void removeStudent(String name) {
            students.removeIf(student -> student.getName().equals(name));
        }

        // Cập nhật thông tin học sinh
        public void updateStudent(String name, Student updatedStudent) {
            for (int i = 0; i < students.size(); i++) {
                if (students.get(i).getName().equals(name)) {
                    students.set(i, updatedStudent);
                }
            }
        }
    }
```
Bước 3: Tạo lớp Main để chạy ứng dụng
```java
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);
            StudentManager studentManager = new StudentManager();

            while (true) {
                System.out.println("\n--- Student Management System ---");
                System.out.println("1. Add student");
                System.out.println("2. Show students");
                System.out.println("3. Remove student");
                System.out.println("4. Update student");
                System.out.println("5. Exit");
                System.out.print("Choose an option: ");

                int choice = scanner.nextInt();
                scanner.nextLine(); // Consume newline character

                switch (choice) {
                    case 1: {
                        System.out.print("Enter student name: ");
                        String name = scanner.nextLine();
                        System.out.print("Enter student age: ");
                        int age = scanner.nextInt();
                        scanner.nextLine(); // Consume newline character
                        System.out.print("Enter class name: ");
                        String className = scanner.nextLine();
                        System.out.print("Enter score: ");
                        double score = scanner.nextDouble();
                        scanner.nextLine(); // Consume newline character

                        Student student = new Student(name, age, className, score);
                        studentManager.addStudent(student);
                        break;
                    }
                    case 2:
                        studentManager.showStudents();
                        break;
                    case 3: {
                        System.out.print("Enter student name to remove: ");
                        String name = scanner.nextLine();
                        studentManager.removeStudent(name);
                        break;
                    }
                    case 4: {
                        System.out.print("Enter student name to update: ");
                        String name = scanner.nextLine();
                        System.out.print("Enter new age: ");
                        int age = scanner.nextInt();
                        scanner.nextLine(); // Consume newline character
                        System.out.print("Enter new class name: ");
                        String className = scanner.nextLine();
                        System.out.print("Enter new score: ");
                        double score = scanner.nextDouble();
                        scanner.nextLine(); // Consume newline character

                        Student updatedStudent = new Student(name, age, className, score);
                        studentManager.updateStudent(name, updatedStudent);
                        break;
                    }
                    case 5:
                        System.out.println("Exiting...");
                        return;
                    default:
                        System.out.println("Invalid option.");
                }
            }
        }
    }
```
### Mô tả:
- Ứng dụng cho phép người dùng thêm, sửa, xóa, và hiển thị danh sách học sinh.
- Dữ liệu học sinh được lưu trữ trong một danh sách (ArrayList).
- Các thao tác này được thực hiện qua giao diện dòng lệnh với các lựa chọn từ người dùng.

## Ứng dụng TODO List
Ứng dụng này sẽ giúp người dùng tạo danh sách công việc cần làm, bao gồm các chức năng như thêm công việc, đánh dấu công việc đã hoàn thành, xóa công việc và hiển thị danh sách công việc.

Các lớp và đối tượng:
- Lớp Task: Lớp này đại diện cho một công việc trong danh sách TODO (chứa tên công việc và trạng thái hoàn thành).
- Lớp TaskManager: Quản lý các công việc, bao gồm các phương thức thêm, xóa, đánh dấu hoàn thành và hiển thị danh sách công việc.
- Lớp Main: Lớp chính để chạy ứng dụng.
Bước 1: Tạo lớp Task
```java
    public class Task {
        private String taskName;
        private boolean isCompleted;

        // Constructor
        public Task(String taskName) {
            this.taskName = taskName;
            this.isCompleted = false;
        }

        // Getter và Setter
        public String getTaskName() {
            return taskName;
        }

        public void setTaskName(String taskName) {
            this.taskName = taskName;
        }

        public boolean isCompleted() {
            return isCompleted;
        }

        public void markAsCompleted() {
            this.isCompleted = true;
        }

        @Override
        public String toString() {
            return taskName + (isCompleted ? " (Completed)" : " (Pending)");
        }
    }
```
Bước 2: Tạo lớp TaskManager
```java
    import java.util.ArrayList;
    import java.util.List;

    public class TaskManager {
        private List<Task> tasks;

        public TaskManager() {
            this.tasks = new ArrayList<>();
        }

        // Thêm công việc
        public void addTask(Task task) {
            tasks.add(task);
        }

        // Hiển thị danh sách công việc
        public void showTasks() {
            if (tasks.isEmpty()) {
                System.out.println("No tasks in the list.");
            } else {
                for (Task task : tasks) {
                    System.out.println(task);
                }
            }
        }

        // Xóa công việc
        public void removeTask(String taskName) {
            tasks.removeIf(task -> task.getTaskName().equals(taskName));
        }

        // Đánh dấu công việc hoàn thành
        public void markAsCompleted(String taskName) {
            for (Task task : tasks) {
                if (task.getTaskName().equals(taskName)) {
                    task.markAsCompleted();
                }
            }
        }
    }
```
Bước 3: Tạo lớp Main để chạy ứng dụng
```java
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);
            TaskManager taskManager = new TaskManager();

            while (true) {
                System.out.println("\n--- TODO List ---");
                System.out.println("1. Add task");
                System.out.println("2. Show tasks");
                System.out.println("3. Remove task");
                System.out.println("4. Mark task as completed");
                System.out.println("5. Exit");
                System.out.print("Choose an option: ");

                int choice = scanner.nextInt();
                scanner.nextLine(); // Consume newline character

                switch (choice) {
                    case 1: {
                        System.out.print("Enter task name: ");
                        String taskName = scanner.nextLine();
                        Task task = new Task(taskName);
                        taskManager.addTask(task);
                        break;
                    }
                    case 2:
                        taskManager.showTasks();
                        break;
                    case 3: {
                        System.out.print("Enter task name to remove: ");
                        String taskName = scanner.nextLine();
                        taskManager.removeTask(taskName);
                        break;
                    }
                    case 4: {
                        System.out.print("Enter task name to mark as completed: ");
                        String taskName = scanner.nextLine();
                        taskManager.markAsCompleted(taskName);
                        break;
                    }
                    case 5:
                        System.out.println("Exiting...");
                        return;
                    default:
                        System.out.println("Invalid option.");
                }
            }
        }
    }
```
### Mô tả:
- Ứng dụng TODO List cho phép người dùng quản lý công việc cần làm.
- Công việc có thể được thêm vào danh sách, đánh dấu là hoàn thành, xóa hoặc hiển thị.
- Các công việc được lưu trữ trong một danh sách (ArrayList).

