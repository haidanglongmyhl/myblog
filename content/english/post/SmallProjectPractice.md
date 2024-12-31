+++ 
title = "Small Project Practice"
date = "2024-12-21"
+++

Below is a detailed guide for two small Java projects: a Student Management Application and a TODO List Application. Both projects will help you familiarize yourself with basic and advanced Java concepts, including exception handling, data structures, object-oriented programming, and basic user interface development.

## Student Management Application
This application will manage student information (name, age, class, and score) and will provide basic functionalities such as adding, updating, deleting, and displaying the list of students.

Classes and Objects:
- **Student Class**: This class will hold the attributes of a student, such as name, age, class, and score.
- **StudentManager Class**: Manages the students, including methods for adding, updating, and deleting students.
- **Main Class**: The main class to run the application.

### Step 1: Create the `Student` class
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

        // Getter and Setter methods
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
Step 2: Create the StudentManager class
```java
    import java.util.ArrayList;
    import java.util.List;

    public class StudentManager {
        private List<Student> students;

        public StudentManager() {
            this.students = new ArrayList<>();
        }

        public void addStudent(Student student) {
            students.add(student);
        }

        public void showStudents() {
            if (students.isEmpty()) {
                System.out.println("No students in the system.");
            } else {
                for (Student student : students) {
                    System.out.println(student);
                }
            }
        }

        public void removeStudent(String name) {
            students.removeIf(student -> student.getName().equals(name));
        }

        public void updateStudent(String name, Student updatedStudent) {
            for (int i = 0; i < students.size(); i++) {
                if (students.get(i).getName().equals(name)) {
                    students.set(i, updatedStudent);
                }
            }
        }
    }
```
Step 3: Create Main class to run the application
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
### Description:
- The application allows users to add, edit, delete, and display student lists.
- Student data is stored in a list (ArrayList).
- These operations are performed via a command line interface with options from the user.ùng.

## Applicatio TODO List
This application will help users create a to-do list, including functions such as adding tasks, marking tasks as completed, deleting tasks, and displaying the task list.

Classes and objects:
- Task class: This class represents a task in the TODO list (containing the task name and completion status).
- TaskManager class: Manages tasks, including methods for adding, deleting, marking completed, and displaying the task list.
- Main class: The main class to run the application.

Step 1: Create the Task class
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
Step 2: Create TaskManager class
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
Step 3: Create Main class to run the application
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
### Description:
- The TODO List application allows users to manage to-do tasks.
- Tasks can be added to the list, marked as complete, deleted or displayed.
- Tasks are stored in a list (ArrayList).

