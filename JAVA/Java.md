# Introduction to Java

Java is a high-level, object-oriented programming language developed by Sun Microsystems in 1995. It is mostly used for building desktop applications, web applications, Android apps, and enterprise systems.
<img width="809" height="405" alt="image" src="https://github.com/user-attachments/assets/ab8c4b2f-308c-4d06-b3eb-24d9c6c7fc0b" />

## Features of Java

- **Object-Oriented Programming (OOP):**  
  Java supports OOP concepts to create modular and reusable code.

- **Platform Independence:**  
  Java programs can run on any operating system with a JVM.

- **Robust and Secure:**  
  Java ensures reliability and security through strong memory management and exception handling.

- **Multithreading and Concurrency:**  
  Java allows concurrent execution of multiple tasks for efficiency.

- **Rich API and Standard Libraries:**  
  Java provides extensive built-in libraries for various programming needs.

- **Frameworks for Enterprise and Web Development:**  
  Java supports frameworks that simplify enterprise and web application development.

- **Open-Source Libraries:**  
  Java has a wide range of libraries to extend functionality and speed up development.
# Understanding the Hello World Program in Java

When we learn any programming language, the first step is writing a simple program to display **"Hello World"**.  
Here is a simple Java program that displays **"Hello World"** on the screen.

## Java Program

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```
Output
Hello World! 

<img width="861" height="371" alt="image" src="https://github.com/user-attachments/assets/1991f91e-bd7b-4d36-94b0-81a80936fd1a" />

# How to Run the Above Code

- Write the code in a file named `HelloWorld.java`.

- The Java Compiler `javac` compiles the program into bytecode and creates a file named `HelloWorld.class`.

- The JVM (Java Virtual Machine) reads the `.class` file and interprets the bytecode.

- The JVM converts the bytecode into machine-readable binary code (such as `001001010`) and then executes the program.

---
<img width="752" height="380" alt="image" src="https://github.com/user-attachments/assets/ab78b301-9539-4ce0-b10e-c98d1b74e4be" />


# Comments in Java

Comments are notes written inside the code to explain what we are doing.  
Comment lines are not executed when the program runs.

## Single-line Comment

```java
// This is a comment

Multi-line Comment
/*
This is a multi-line comment.
This is useful for explaining larger sections of code.
*/


# Famous Applications Built Using Java

## Android Apps
Most Android mobile applications are built using Java.

## Netflix
Uses Java for content delivery and backend services.

## Amazon
Java is widely used in Amazon’s backend systems.

## LinkedIn
Uses Java for handling high traffic and scalability.

## Minecraft
One of the world’s most popular games built using Java.

## Spotify
Uses Java in parts of its server-side infrastructure.

## Uber
Java is used for backend services such as trip management.

## NASA WorldWind
A virtual globe software application built using Java.
- **Maintainability and Scalability:**  
  Java’s structured design allows easy maintenance and growth of applications.


# Differences Between JDK, JRE and JVM

- **JDK (Java Development Kit):**  
  Provides tools and libraries to develop Java applications. It includes JRE and development tools such as the Java compiler (`javac`).

- **JRE (Java Runtime Environment):**  
  Provides the libraries and JVM required to run Java programs.

- **JVM (Java Virtual Machine):**  
  Executes the compiled Java bytecode on the system.

> **Note:** Java bytecode can run on any machine with a JVM, but JVM implementations are platform-dependent for each operating system.

<img width="886" height="377" alt="image" src="https://github.com/user-attachments/assets/f52b7044-8d3b-4261-9fe9-dba18e265680" />

---

# How JVM Works - JVM Architecture

The **Java Virtual Machine (JVM)** is a core component of the **Java Runtime Environment (JRE)** that allows Java programs to run on any platform without modification.

JVM acts as an interpreter between Java bytecode and the underlying hardware, providing Java’s famous **Write Once, Run Anywhere (WORA)** capability.

## JVM Working Process

- Java source code (`.java`) is compiled by `javac` into bytecode (`.class`).

- JVM loads the bytecode, verifies it, links it, and then executes it.

- Execution may involve interpreting bytecode or using **Just-In-Time (JIT)** compilation to convert frequently used code into native machine code for better performance.

- Garbage Collection runs in the background to reclaim memory from unused objects.

---

# Architecture of JVM

The JVM architecture consists of several important components that work together to execute Java programs efficiently.
<img width="864" height="425" alt="image" src="https://github.com/user-attachments/assets/6268da82-3f94-4f64-9fd3-750764c307b4" />



## Components of JVM Architecture

### 1. Class Loader Subsystem

The Class Loader Subsystem is mainly responsible for loading class files into memory.
<img width="879" height="502" alt="image" src="https://github.com/user-attachments/assets/01c54206-a8b8-4364-9318-c4f0b9a37445" />

### Activities of Class Loader

#### Loading

- Reads `.class` files and stores class metadata in the **Method Area**.

- Creates a `Class` object in the heap representing the loaded class.

## Example Program

```java
class GFG {

    static {
        System.out.println("GFG class is loaded by the JVM!");
    }

    public void display() {
        System.out.println("Method of GFG class is executed.");
    }
}

public class Test {

    public static void main(String[] args) throws Exception {

        System.out.println("Main method started.");

        // Loading the class explicitly using Class.forName()
        Class.forName("GFG");

        System.out.println("Class loaded successfully.");

        // Creating object to execute method
        GFG obj = new GFG();
        obj.display();
    }
}


Output
Main method started.
GFG class is loaded by the JVM!
Class loaded successfully.
Method of GFG class is executed.
