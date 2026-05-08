# ☕ Java Programming Digital Book

> A Beginner-Friendly Digital Handbook to Learn Java Step-by-Step

---

# 📚 Table of Contents

- [📖 Introduction to Java](#-introduction-to-java)
- [✨ Features of Java](#-features-of-java)
- [👋 Hello World Program in Java](#-hello-world-program-in-java)
- [⚙️ How Java Code Runs](#️-how-java-code-runs)
- [💬 Comments in Java](#-comments-in-java)
- [🌍 Famous Applications Built Using Java](#-famous-applications-built-using-java)
- [🧩 Differences Between JDK, JRE, and JVM](#-differences-between-jdk-jre-and-jvm)
- [🖥️ How JVM Works](#️-how-jvm-works)
- [🏗️ JVM Architecture](#️-jvm-architecture)
- [📦 Class Loader Subsystem](#-class-loader-subsystem)
- [🧪 Class Loading Example](#-class-loading-example)
- [🎯 Conclusion](#-conclusion)

---

# 📖 Introduction to Java

Java is a **high-level**, **object-oriented programming language** developed by **Sun Microsystems** in **1995**.

It is widely used for:

- Desktop Applications
- Web Applications
- Android Applications
- Enterprise Systems
- Cloud-Based Applications

---

## 🖼️ Java Overview

![Java Introduction](https://github.com/user-attachments/assets/ab8c4b2f-308c-4d06-b3eb-24d9c6c7fc0b)

---

# ✨ Features of Java

<details>
<summary><strong>🔹 Object-Oriented Programming (OOP)</strong></summary>

Java supports OOP concepts like:

- Class
- Object
- Inheritance
- Polymorphism
- Abstraction
- Encapsulation

This helps create modular and reusable applications.

</details>

---

<details>
<summary><strong>🔹 Platform Independence</strong></summary>

Java follows the principle:

> **Write Once, Run Anywhere (WORA)**

Java programs can run on any operating system that has a JVM installed.

</details>

---

<details>
<summary><strong>🔹 Robust and Secure</strong></summary>

Java provides:

- Strong memory management
- Exception handling
- Type checking
- Secure runtime environment

</details>

---

<details>
<summary><strong>🔹 Multithreading and Concurrency</strong></summary>

Java supports executing multiple tasks simultaneously for better performance.

</details>

---

<details>
<summary><strong>🔹 Rich API and Libraries</strong></summary>

Java contains extensive built-in libraries for:

- Networking
- File Handling
- Collections
- GUI
- Database Connectivity

</details>

---

<details>
<summary><strong>🔹 Enterprise Framework Support</strong></summary>

Popular Java frameworks:

- Spring Boot
- Hibernate
- Struts
- JavaFX

</details>

---

# 👋 Hello World Program in Java

The first Java program every beginner writes is the famous:

> **Hello World Program**

---

## 💻 Java Code

```java
public class HelloWorld {

    public static void main(String[] args) {

        System.out.println("Hello World!");

    }
}
```

---

# ✅ Output

```text
Hello World!
```

---

## 🖼️ Output Screenshot

![Hello World Output](https://github.com/user-attachments/assets/1991f91e-bd7b-4d36-94b0-81a80936fd1a)

---

# ⚙️ How Java Code Runs

<details>
<summary><strong>📌 Step-by-Step Execution Process</strong></summary>

### Step 1️⃣ — Write the Program

Save the file as:

```text
HelloWorld.java
```

---

### Step 2️⃣ — Compile the Program

Use Java Compiler:

```bash
javac HelloWorld.java
```

This generates:

```text
HelloWorld.class
```

---

### Step 3️⃣ — JVM Executes Bytecode

Run the program:

```bash
java HelloWorld
```

The JVM converts bytecode into machine-readable instructions.

</details>

---

## 🖼️ Java Execution Flow

![Java Execution](https://github.com/user-attachments/assets/ab78b301-9539-4ce0-b10e-c98d1b74e4be)

---

# 💬 Comments in Java

Comments are notes inside code used to explain logic.

They are ignored during execution.

---

## 🔹 Single-Line Comment

```java
// This is a comment
```

---

## 🔹 Multi-Line Comment

```java
/*
This is a multi-line comment.
Used for explaining larger sections of code.
*/
```

---

# 🌍 Famous Applications Built Using Java

<details>
<summary><strong>📱 Android Applications</strong></summary>

Most Android applications use Java.

</details>

---

<details>
<summary><strong>🎬 Netflix</strong></summary>

Uses Java for backend systems and content delivery.

</details>

---

<details>
<summary><strong>🛒 Amazon</strong></summary>

Java powers many backend services at Amazon.

</details>

---

<details>
<summary><strong>💼 LinkedIn</strong></summary>

Uses Java for scalability and handling massive traffic.

</details>

---

<details>
<summary><strong>🎮 Minecraft</strong></summary>

One of the world's most popular Java-based games.

</details>

---

<details>
<summary><strong>🎵 Spotify</strong></summary>

Uses Java in server-side infrastructure.

</details>

---

<details>
<summary><strong>🚗 Uber</strong></summary>

Java handles trip management and backend services.

</details>

---

<details>
<summary><strong>🌎 NASA WorldWind</strong></summary>

A virtual globe application built using Java.

</details>

---

# 🧩 Differences Between JDK, JRE and JVM

| Component | Description |
|---|---|
| **JDK** | Java Development Kit used for developing Java applications |
| **JRE** | Java Runtime Environment used for running Java programs |
| **JVM** | Java Virtual Machine that executes Java bytecode |

---

## 📌 Relationship

```text
JDK = JRE + Development Tools
JRE = JVM + Libraries
```

---

> ⚠️ Note:
>
> JVM implementations are platform-dependent, but Java bytecode remains platform-independent.

---

## 🖼️ JDK vs JRE vs JVM

![JDK JRE JVM](https://github.com/user-attachments/assets/f52b7044-8d3b-4261-9fe9-dba18e265680)

---

# 🖥️ How JVM Works

The **Java Virtual Machine (JVM)** acts as an interpreter between Java bytecode and hardware.

It enables Java's famous:

# ✨ Write Once, Run Anywhere (WORA)

---

## 🔄 JVM Working Process

<details>
<summary><strong>📌 JVM Execution Flow</strong></summary>

### 1️⃣ Java Source Code

```text
.java
```

↓

### 2️⃣ Java Compiler (`javac`)

Converts source code into bytecode.

↓

### 3️⃣ Bytecode File

```text
.class
```

↓

### 4️⃣ JVM Loads Bytecode

- Verification
- Linking
- Initialization

↓

### 5️⃣ Execution Engine

Uses:

- Interpreter
- JIT Compiler

↓

### 6️⃣ Native Machine Code Execution

Program runs successfully.

</details>

---

# 🏗️ JVM Architecture

The JVM architecture contains multiple components working together.

---

## 🖼️ JVM Architecture Diagram

![JVM Architecture](https://github.com/user-attachments/assets/6268da82-3f94-4f64-9fd3-750764c307b4)

---

# 📦 Class Loader Subsystem

The **Class Loader Subsystem** loads Java classes into memory.

---

## 🖼️ Class Loader Diagram

![Class Loader](https://github.com/user-attachments/assets/01c54206-a8b8-4364-9318-c4f0b9a37445)

---

# 🔍 Activities of Class Loader

<details>
<summary><strong>📌 Loading</strong></summary>

- Reads `.class` files
- Stores metadata into Method Area
- Creates `Class` objects inside Heap Memory

</details>

---

<details>
<summary><strong>📌 Linking</strong></summary>

Linking contains:

- Verification
- Preparation
- Resolution

</details>

---

<details>
<summary><strong>📌 Initialization</strong></summary>

Static variables and static blocks are initialized.

</details>

---

# 🧪 Class Loading Example

## 💻 Java Program

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

        // Loading class explicitly
        Class.forName("GFG");

        System.out.println("Class loaded successfully.");

        // Creating object
        GFG obj = new GFG();
        obj.display();
    }
}
```

---

# ✅ Output

```text
Main method started.
GFG class is loaded by the JVM!
Class loaded successfully.
Method of GFG class is executed.
```

---

# 🎯 Conclusion

Java is one of the most powerful and widely used programming languages in the world.

It provides:

- Platform Independence
- Strong Security
- Scalability
- Rich Libraries
- Enterprise-Level Performance

Learning Java builds a strong foundation for:

- Software Development
- Android Development
- Backend Engineering
- Cloud Computing
- Enterprise Applications

---

# 🚀 Happy Coding with Java ☕
