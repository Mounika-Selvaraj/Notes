# Basics of Java  
## A Digital Book for Beginners

![Java Introduction](https://github.com/user-attachments/assets/ab8c4b2f-308c-4d06-b3eb-24d9c6c7fc0b)

Java is one of the most popular programming languages in the world. It is widely used for building desktop applications, web applications, Android applications, enterprise software, backend systems, and large-scale distributed platforms. Java is known for its simplicity, object-oriented structure, platform independence, and strong runtime performance.

---

# Table of Contents
### Java Basics
- [1. What is Java?](#1-what-is-java)
- [2. JVM, JDK, and JRE](#2-jvm-jdk-and-jre)
- [3. Installing Java and Setting Up the Environment](#3-installing-java-and-setting-up-the-environment)
- [4. First Program: Hello World](#4-first-program-hello-world)
- [5. Compilation vs Execution](#5-compilation-vs-execution)
- [6. JVM Architecture](#6-jvm-architecture)
- [7. Notes for Beginners](#7-notes-for-beginners)

---

### Syntax & Core Concepts

- [1. Variables & Data Types](#1-variables--data-types)
- [2. Operators](#2-operators)
- [3. Type Casting](#3-type-casting)
- [4. Control Flow](#4-control-flow)
- [5. if, else, switch](#5-if-else-switch)
- [6. Loops](#6-loops)
- [7. break and continue](#7-break-and-continue)

---

<details>
<summary><strong>1. What is Java?</strong></summary>

Java is a high-level, object-oriented programming language developed by Sun Microsystems in 1995. It was designed with the idea that code should be portable, secure, and easy to maintain. Java programs are compiled into bytecode, which can run on any device that has a JVM.

## Why Java is important
- Java is simple enough for beginners but powerful enough for large enterprise systems.
- Java supports object-oriented programming, which helps in writing reusable and modular code.
- Java is platform-independent because the compiled bytecode can run on different operating systems.
- Java has a large ecosystem of libraries, tools, and frameworks.

## Where Java is used
- Android applications.
- Web applications.
- Desktop applications.
- Enterprise software.
- Backend services.
- Scientific and distributed systems.

## Core idea of Java
Write code once, compile it into bytecode, and run it anywhere using the JVM.

</details>

---

<details>
<summary><strong>2. JVM, JDK, and JRE</strong></summary>

These three terms are the foundation of Java. Beginners often mix them up, but each one has a separate role in the Java ecosystem.

## JVM
The Java Virtual Machine is the engine that runs Java bytecode. It reads the compiled `.class` file and executes it on the computer. The JVM makes Java platform-independent because the same bytecode can run on different systems with different JVM implementations.

## JRE
The Java Runtime Environment contains the libraries and the JVM required to run Java applications. If you only want to run Java programs, the JRE is enough.

## JDK
The Java Development Kit contains everything needed to develop Java programs. It includes the JRE, the JVM, and development tools such as `javac`, the Java compiler.

## Relationship between them
- JDK = JRE + development tools.
- JRE = JVM + core libraries.
- JVM = executes bytecode.

## Simple memory trick
- **JDK** = for developers.
- **JRE** = for users who run programs.
- **JVM** = the execution engine inside both.

![JDK JRE JVM](https://github.com/user-attachments/assets/f52b7044-8d3b-4261-9fe9-dba18e265680)

</details>

---

<details>
<summary><strong>3. Installing Java and Setting Up the Environment</strong></summary>

Before writing and running Java programs, you need to install the JDK and configure your system properly. This setup lets you compile Java code from the command line and run it using the JVM.

## What you need to install
- Java Development Kit, usually the latest stable version.
- A text editor or IDE such as VS Code, IntelliJ IDEA, or Eclipse.
- Command-line access to verify installation.

## General installation steps
1. Download the JDK from the official Java distribution.
2. Install it on your system.
3. Set the environment variables.
4. Verify installation using terminal or command prompt.

## Environment setup
You usually need to configure:
- `JAVA_HOME`, which points to the JDK folder.
- `PATH`, which includes the `bin` directory of the JDK.

## Why environment variables matter
When `PATH` is set correctly, you can use `javac` and `java` from any folder in the terminal. Without this, the system may not recognize Java commands.

## Verification commands
```bash
java -version
javac -version
```

If both commands return version information, Java is installed correctly.

![Java installation](https://github.com/user-attachments/assets/01c54206-a8b6-4364-9318-c4f0b9a37445)

</details>

---

<details>
<summary><strong>4. First Program: Hello World</strong></summary>

The `Hello World` program is the traditional first step in learning a new programming language. It helps you understand the basic structure of a Java program, class definition, main method, and output statement.

## Java code
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

## Line-by-line explanation
### `public class HelloWorld`
This creates a class named `HelloWorld`. In Java, every program is written inside a class.

### `public static void main(String[] args)`
This is the entry point of the program. The JVM starts execution from this method.

### `System.out.println("Hello World!");`
This prints text to the screen and moves the cursor to the next line.

## Output
```text
Hello World!
```

## Important rules
- The file name must match the public class name.
- If the class is `HelloWorld`, the file must be `HelloWorld.java`.
- Java is case-sensitive.
- Every statement usually ends with a semicolon.

## What this teaches
This small program introduces the most important building blocks of Java programming:
- Class.
- Main method.
- Statement execution.
- Console output.

![Hello World output](https://github.com/user-attachments/assets/1991f91e-bd7b-4d36-94b0-81a80936fd1a)

</details>

---

<details>
<summary><strong>5. Compilation vs Execution</strong></summary>

Compilation and execution are two different stages in Java program flow. Understanding this difference is essential because Java does not run source code directly.

## Compilation
Compilation means converting human-readable `.java` source code into bytecode. The Java compiler is `javac`. After compilation, a `.class` file is created.

## Execution
Execution means running the compiled bytecode using the JVM. The JVM reads the `.class` file and translates it into machine instructions that the operating system can execute.

## Example flow
1. Write `HelloWorld.java`.
2. Compile using `javac HelloWorld.java`.
3. Create `HelloWorld.class`.
4. Run using `java HelloWorld`.
5. JVM executes the bytecode.

## Why Java uses this model
This two-step process helps Java achieve portability and security. Bytecode can be verified before execution, which makes Java safer than directly running raw machine code.

## Comparison table

| Topic | Compilation | Execution |
|---|---|---|
| Tool | `javac` | `java` |
| Input | `.java` file | `.class` file |
| Output | Bytecode | Running program output |
| Role | Converts source to bytecode | Executes bytecode |
| Component | Java compiler | JVM |

</details>

---

<details>
<summary><strong>6. JVM Architecture</strong></summary>

The JVM architecture describes how Java bytecode is loaded, verified, executed, and managed in memory. This architecture is one of the main reasons Java is widely used for reliable and scalable software.

## Main JVM parts
- Class Loader Subsystem.
- Runtime Data Areas.
- Execution Engine.
- Native Method Interface.
- Garbage Collector.

## Class Loader Subsystem
The class loader loads `.class` files into memory. It is responsible for reading class metadata and preparing classes for use. It helps Java load classes dynamically at runtime.

## Runtime Data Areas
These are memory areas used by the JVM during execution. They store class information, objects, stacks, and execution state.

## Execution Engine
The execution engine runs bytecode. It may interpret bytecode or use JIT compilation to improve performance for frequently used code.

## Garbage Collection
Garbage collection automatically removes objects that are no longer needed, freeing memory and reducing manual memory handling.

## JVM working idea
- `.java` is compiled into `.class`.
- JVM loads the bytecode.
- JVM verifies and links the code.
- JVM executes the code.
- Garbage collection manages memory.

![JVM architecture](https://github.com/user-attachments/assets/6268da82-3f94-4f64-9fd3-750764c307b4)

</details>

---

<details>
<summary><strong>7. Notes for Beginners</strong></summary>

Java becomes much easier when you understand a few simple ideas well. These notes are useful when you are starting out.

## Key beginner notes
- Java is object-oriented, so classes and objects are central concepts.
- Java code is compiled, not interpreted directly like scripting languages.
- The JVM allows the same code to run on different operating systems.
- The `main` method is the starting point of every Java application.
- `javac` compiles code, while `java` runs the compiled program.

## Common beginner mistakes
- Using the wrong file name for the public class.
- Forgetting semicolons.
- Confusing JDK, JRE, and JVM.
- Trying to run `.java` files directly instead of compiling first.
- Not setting the `PATH` variable correctly.

## Easy way to remember the Java flow
**Write code → Compile code → Run bytecode → JVM executes**

## Final understanding
If you understand Java basics, the role of JDK/JRE/JVM, the installation setup, the Hello World program, and the compilation-execution process, you already have a strong foundation for learning the rest of Java.

</details>

---
# Java Basics: Syntax and Core Concepts


Java is a high-level, object-oriented programming language used to build applications for desktop, web, Android, and enterprise systems. It is known for its clean syntax, portability, strong memory management, and powerful runtime environment.


---

<details>
<summary><strong>1. Syntax & Core Concepts</strong></summary>

Java syntax is the set of rules that defines how Java programs are written. A Java program is usually organized into classes and methods, and execution begins from the `main` method.

## Basic structure of a Java program
```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
```

## Core syntax rules
- Every Java program must be written inside a class.
- The `main` method is the entry point of execution.
- Statements usually end with a semicolon `;`.
- Java is case-sensitive.
- Braces `{}` define blocks of code.
- A file containing a public class must have the same name as the class.

## Important core concepts
- **Class:** A blueprint for objects.
- **Object:** An instance of a class.
- **Method:** A block of code that performs a task.
- **Statement:** A single instruction in a program.
- **Block:** A group of statements enclosed in braces.

## Example
```java
class Demo {
    public static void main(String[] args) {
        System.out.println("This is Java syntax.");
    }
}
```

## Why syntax matters
Correct syntax allows the compiler to understand the program. Even a small mistake like a missing semicolon or wrong bracket can cause an error.

</details>

---

<details>
<summary><strong>2. Variables & Data Types</strong></summary>

Variables are used to store values in memory. In Java, every variable must have a data type, which tells the compiler what kind of value it will store.

## What is a variable?
A variable is a named memory location that holds data which can change during program execution.

## Variable declaration
```java
int age = 20;
String name = "Mounika";
double salary = 45000.50;
```

## Types of variables
- **Local variable:** Declared inside a method.
- **Instance variable:** Declared inside a class but outside methods.
- **Static variable:** Shared by all objects of a class.

## Java data types
Java data types are broadly divided into two categories:
- **Primitive data types**
- **Non-primitive data types**

## Primitive data types
- `byte`
- `short`
- `int`
- `long`
- `float`
- `double`
- `char`
- `boolean`

## Example
```java
int marks = 95;
char grade = 'A';
boolean passed = true;
```

## Non-primitive data types
- `String`
- Arrays
- Classes
- Interfaces

## Why data types are important
- They define the kind of value stored.
- They determine memory usage.
- They help prevent invalid operations.

## Example with multiple variables
```java
class Student {
    public static void main(String[] args) {
        String studentName = "Anu";
        int rollNumber = 101;
        float percentage = 89.5f;
        boolean isPresent = true;

        System.out.println(studentName);
    }
}
```

</details>

---

<details>
<summary><strong>3. Operators</strong></summary>

Operators are symbols used to perform operations on variables and values. Java provides many types of operators, but the most common ones are arithmetic, logical, and bitwise operators.

## Arithmetic operators
These are used for mathematical calculations.

- `+` Addition
- `-` Subtraction
- `*` Multiplication
- `/` Division
- `%` Modulus

### Example
```java
int a = 10;
int b = 3;
System.out.println(a + b);
System.out.println(a % b);
```

## Logical operators
These are used to combine conditions.

- `&&` Logical AND
- `||` Logical OR
- `!` Logical NOT

### Example
```java
boolean x = true;
boolean y = false;
System.out.println(x && y);
System.out.println(x || y);
System.out.println(!x);
```

## Bitwise operators
These operate at the bit level.

- `&` Bitwise AND
- `|` Bitwise OR
- `^` Bitwise XOR
- `~` Bitwise NOT
- `<<` Left shift
- `>>` Right shift

### Example
```java
int a = 5;
int b = 3;
System.out.println(a & b);
System.out.println(a | b);
System.out.println(a << 1);
```

## Why operators matter
Operators let you build expressions, compare values, and control program logic. They are used in calculations, conditions, loops, and many real-world programs.

![Java operators](https://github.com/user-attachments/assets/ab8c4b2f-308c-4d06-b3eb-24d9c6c7fc0b)

</details>

---

<details>
<summary><strong>4. Type Casting</strong></summary>

Type casting means converting one data type into another. In Java, this is useful when one type must be changed for calculation, storage, or compatibility.

## Types of casting
### Widening casting
This happens automatically when a smaller type is converted into a larger type.

```java
int num = 100;
double value = num;
```

### Narrowing casting
This happens manually when a larger type is converted into a smaller type.

```java
double value = 9.78;
int num = (int) value;
```

## Example
```java
class CastingDemo {
    public static void main(String[] args) {
        int a = 10;
        double b = a;        // widening
        double c = 12.5;
        int d = (int) c;     // narrowing

        System.out.println(b);
        System.out.println(d);
    }
}
```

## Key points
- Widening is safe and automatic.
- Narrowing may cause data loss.
- Explicit casting uses parentheses like `(int)`.

## When to use it
Type casting is useful in arithmetic expressions, handling user input, converting floating-point values to integers, and working with mixed data types.

</details>

---

<details>
<summary><strong>5. Control Flow</strong></summary>

Control flow determines the order in which statements are executed. Java uses conditional statements and loops to control program behavior based on conditions.

## Why control flow is important
Programs often need to make decisions, repeat tasks, or stop execution under certain conditions. Control flow makes this possible.

## Main control flow tools
- `if`
- `else`
- `switch`
- `for`
- `while`
- `do-while`
- `break`
- `continue`

## Decision-making
Java evaluates conditions and chooses which block of code to execute. This helps programs respond to different situations.

## Repetition
Loops allow a block of code to run multiple times until a condition changes.

</details>

---

<details>
<summary><strong>6. if, else, switch</strong></summary>

These statements are used to make decisions in Java.

## if statement
The `if` statement runs a block only when the condition is true.

```java
int age = 18;
if (age >= 18) {
    System.out.println("Eligible to vote");
}
```

## if-else statement
The `else` block runs when the condition is false.

```java
int marks = 40;
if (marks >= 50) {
    System.out.println("Pass");
} else {
    System.out.println("Fail");
}
```

## if-else-if ladder
This is used when there are multiple conditions.

```java
int score = 75;
if (score >= 90) {
    System.out.println("A grade");
} else if (score >= 75) {
    System.out.println("B grade");
} else {
    System.out.println("C grade");
}
```

## switch statement
The `switch` statement is used when one variable can match many possible values.

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

## When to use what
- Use `if` for simple conditions.
- Use `if-else` for two outcomes.
- Use `switch` when checking many fixed values.

</details>

---

<details>
<summary><strong>7. Loops</strong></summary>

Loops repeat a block of code multiple times. Java supports three major loops: `for`, `while`, and `do-while`.

## for loop
The `for` loop is used when the number of iterations is known.

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

## while loop
The `while` loop runs as long as the condition is true.

```java
int i = 1;
while (i <= 5) {
    System.out.println(i);
    i++;
}
```

## do-while loop
The `do-while` loop executes at least once, even if the condition is false.

```java
int i = 1;
do {
    System.out.println(i);
    i++;
} while (i <= 5);
```

## Differences between loops
- `for` is best when iterations are predictable.
- `while` is useful when the condition controls repetition.
- `do-while` is useful when the block must run at least once.

## Example use case
Loops are commonly used in menus, arrays, input validation, searching, and repeated calculations.

</details>

---

<details>
<summary><strong>8. break and continue</strong></summary>

`break` and `continue` are loop control statements used to change the normal flow of loops.

## break statement
The `break` statement exits the loop immediately.

```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        break;
    }
    System.out.println(i);
}
```

## continue statement
The `continue` statement skips the current iteration and moves to the next one.

```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        continue;
    }
    System.out.println(i);
}
```

## Difference
- `break` stops the loop completely.
- `continue` skips only one iteration.

## Where they are useful
- Exiting a loop when a target is found.
- Skipping invalid or unwanted values.
- Controlling nested or conditional loops.

## Example in a real program
If you are reading numbers and want to stop when a special value appears, use `break`. If you want to ignore one bad value and keep processing, use `continue`.

</details>

---
