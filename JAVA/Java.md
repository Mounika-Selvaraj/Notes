# Basics of Java  
## A Digital Book for Beginners

![Java Introduction](https://github.com/user-attachments/assets/ab8c4b2f-308c-4d06-b3eb-24d9c6c7fc0b)

Java is one of the most popular programming languages in the world. It is widely used for building desktop applications, web applications, Android applications, enterprise software, backend systems, and large-scale distributed platforms. Java is known for its simplicity, object-oriented structure, platform independence, and strong runtime performance.

---

# Table of Contents

- [1. What is Java?](#1-what-is-java)
- [2. JVM, JDK, and JRE](#2-jvm-jdk-and-jre)
- [3. Installing Java and Setting Up the Environment](#3-installing-java-and-setting-up-the-environment)
- [4. First Program: Hello World](#4-first-program-hello-world)
- [5. Compilation vs Execution](#5-compilation-vs-execution)
- [6. JVM Architecture](#6-jvm-architecture)
- [7. Notes for Beginners](#7-notes-for-beginners)

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

![Java basics](https://github.com/user-attachments/assets/ab78b301-9539-4ce0-b10e-c98d1b74e4be)

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

![Compilation and execution](https://github.com/user-attachments/assets/ab78b301-9539-4ce0-b10e-c98d1b74e4be)

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

![Java learning path](https://github.com/user-attachments/assets/f52b7044-8d3b-4261-9fe9-dba18e265680)

</details>

---

# End of Book

Java is one of the best languages for building a strong programming foundation. Once the basics are clear, moving into variables, operators, loops, methods, arrays, and object-oriented programming becomes much easier.
