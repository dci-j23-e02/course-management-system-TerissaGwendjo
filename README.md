### Level of Difficulty: Intermediate
### Title: Java Course Management System
### Overview: 
In this assignment, you will be creating a Java Course Management System. This system will be responsible for managing the courses and their related files. You will be using the java.io.FileInputStream, java.io.FileOutputStream, and java.io.IOException classes to handle file input and output operations. The system should be able to read course files, write updates to these files, handle any file-related errors, take attendance, read student details, and add a teacher to the course. The system will be console-based, and users will interact with it using text commands.

**Tasks:**
1. **Task1: Reading Course Files**
You need to create a method that uses FileInputStream to read course files. The method should take the file name as a parameter and return the content of the file.

**Explaining how to solve it:**
You can solve this task by creating a FileInputStream object and passing the file name to its constructor. Then, use a while loop to read the file content byte by byte until the end of the file.

**Example code : **
```java
public String readCourseFile(String fileName) {
    String content = "";
    try {
        FileInputStream fis = new FileInputStream(fileName);
        int i;
        while ((i = fis.read()) != -1) {
            content += (char) i;
        }
        fis.close();
    } catch (IOException e) {
        e.printStackTrace();
    }
    return content;
}
```

2. **Task2: Writing Updates to Course Files**
You need to create a method that uses FileOutputStream to write updates to course files. The method should take the file name and the new content as parameters.

**Explaining how to solve it:**
You can solve this task by creating a FileOutputStream object and passing the file name to its constructor. Then, use the write method to write the new content to the file.

**Example code : **
```java
public void writeCourseFile(String fileName, String newContent) {
    try {
        FileOutputStream fos = new FileOutputStream(fileName);
        byte[] bytes = newContent.getBytes();
        fos.write(bytes);
        fos.close();
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

3. **Task3: Handling File-Related Errors**
You need to modify the methods from the previous tasks to handle any file-related errors using IOException.

**Explaining how to solve it:**
You can solve this task by adding a catch block for IOException in the try-catch statement. In the catch block, you can print the error message.

**Example code : **
```java
public String readCourseFile(String fileName) {
    String content = "";
    try {
        FileInputStream fis = new FileInputStream(fileName);
        int i;
        while ((i = fis.read()) != -1) {
            content += (char) i;
        }
        fis.close();
    } catch (IOException e) {
        System.out.println("An error occurred while reading the file: " + e.getMessage());
    }
    return content;
}
```

4. **Task4: Taking Attendance**
You need to create a method that takes attendance for a course. The method should take the course name and a list of student names as parameters, and write the attendance to a file.

**Explaining how to solve it:**
You can solve this task by creating a FileOutputStream object and passing the attendance file name to its constructor. Then, use the write method to write the attendance to the file.

**Example code : **
```java
public void takeAttendance(String courseName, List<String> studentNames) {
    String fileName = courseName + "_attendance.txt";
    try {
        FileOutputStream fos = new FileOutputStream(fileName);
        for (String name : studentNames) {
            fos.write((name + "\n").getBytes());
        }
        fos.close();
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

5. **Task5: Reading Student Details**
You need to create a method that reads student details from a file. The method should take the file name as a parameter and return a list of student names.

**Explaining how to solve it:**
You can solve this task by creating a FileInputStream object and passing the student details file name to its constructor. Then, use a while loop to read the file content line by line until the end of the file.

**Example code : **
```java
public List<String> readStudentDetails(String fileName) {
    List<String> studentNames = new ArrayList<>();
    try {
        FileInputStream fis = new FileInputStream(fileName);
        Scanner scanner = new Scanner(fis);
        while (scanner.hasNextLine()) {
            studentNames.add(scanner.nextLine());
        }
        fis.close();
    } catch (IOException e) {
        e.printStackTrace();
    }
    return studentNames;
}
```

6. **Task6: Adding a Teacher to the Course**
You need to create a method that adds a teacher to a course. The method should take the course name and the teacher name as parameters, and write the teacher name to the course file.

**Explaining how to solve it:**
You can solve this task by creating a FileOutputStream object and passing the course file name to its constructor. Then, use the write method to write the teacher name to the course file.

**Example code : **
```java
public void addTeacher(String courseName, String teacherName) {
    String fileName = courseName + ".txt";
    try {
        FileOutputStream fos = new FileOutputStream(fileName, true);
        fos.write(("Teacher: " + teacherName + "\n").getBytes());
        fos.close();
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

**Examples:**
Input: readCourseFile("course1.txt")
Output: "Course Name: Java Programming\nCourse Description: Learn the basics of Java programming."

**Notes:** 
Make sure to close the FileInputStream and FileOutputStream in a finally block to ensure that the resources are always released regardless of whether an exception is thrown or not.

**Bonus:** 
For extra credit, enhance the system by adding more features, such as adding new courses, deleting courses, or searching for a specific course.
