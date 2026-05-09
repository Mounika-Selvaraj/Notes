# 🔹 Java Packages and Access Modifiers – Detailed Notes

## Table of Contents

- [1. What is a Java Package?](#1-what-is-a-java-package)
- [2. Why Use Packages?](#2-why-use-packages)
- [3. Creating Packages](#3-creating-packages)
  - [3.1 Directory Structure](#31-directory-structure)
  - [3.2 Declaring a Package in Java](#32-declaring-a-package-in-java)
  - [3.3 Compiling and Running Package Classes](#33-compiling-and-running-package-classes)
- [4. Importing Classes from Packages](#4-importing-classes-from-packages)
  - [4.1 Importing a Single Class](#41-importing-a-single-class)
  - [4.2 Importing All Classes in a Package](#42-importing-all-classes-in-a-package)
  - [4.3 Static Imports](#43-static-imports)
- [5. Access Modifiers in Java](#5-access-modifiers-in-java)
  - [5.1 Overview of Access Modifiers](#51-overview-of-access-modifiers)
  - [5.2 public](#52-public)
  - [5.3 private](#53-private)
  - [5.4 protected](#54-protected)
  - [5.5 default (package‑private)](#55-default-package-private)
- [6. Access Modifiers – Detailed Table](#6-access-modifiers-detailed-table)
- [7. Usage Examples of Access Modifiers](#7-usage-examples-of-access-modifiers)
  - [7.1 public usage](#71-public-usage)
  - [7.2 private usage](#72-private-usage)
  - [7.3 protected usage](#73-protected-usage)
  - [7.4 default access usage](#74-default-access-usage)
- [8. Best Practices for Packages and Access Modifiers](#8-best-practices-for-packages-and-access-modifiers)
- [9. Common Interview‑Style Questions](#9-common-interview-style-questions)

---

## 1. What is a Java Package?

A **package** in Java is a **namespace** that organizes related classes, interfaces, and sub‑packages into a single unit.

It helps:
- Avoid **name conflicts** (e.g., two classes named `Student` in different packages).
- Control **access** to classes and members using access modifiers.
- Make the code **modular** and **maintainable**.

Example:
```java
package com.example.bank;
```

Here, `com.example.bank` is the fully qualified package name.

---

## 2. Why Use Packages?

Key reasons to use packages:

- **Group related classes** (e.g., `com.example.bank.accounts`, `com.example.bank.loan`).
- **Avoid naming collisions** across different modules.
- **Control access** using `public`, `private`, `protected`, and *default*.
- **Reuse code** via JARs and libraries (e.g., `java.util`, `java.io`).
- **Make the project structure clean** and professional.

---

## 3. Creating Packages

### 3.1 Directory Structure

In Java, **package names correspond directly to directory structure**.

For example, the package:

```java
package com.example.bank;
```

Means:
- The source file should be placed in the directory path:  
  `com/example/bank/`.
- The root folder (e.g., `src`) is the **source root**.
```
Example file system:
src/
com/
example/
bank/
Account.java
BankMain.java
```


Here:
- `Account.java` declares `package com.example.bank;`.
- `BankMain.java` also declares `package com.example.bank;`.

### 3.2 Declaring a Package in Java

Use the `package` keyword at the **top of the Java file**, before any class or import statement.

```java
// File: com/example/bank/Account.java

package com.example.bank;

public class Account {
    private double balance;

    public Account(double initialBalance) {
        this.balance = initialBalance;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
}
```

Notes:
- `package` must be **first meaningful statement** (comments are allowed before).
- A file can have **only one package** declaration.

### 3.3 Compiling and Running Package Classes
```
Assume the directory structure is:
src/
com/
example/
bank/
Account.java
BankMain.java
```

#### Compiling:

From the **root of the project** (e.g., location containing `src`):

```bash
javac src/com/example/bank/*.java
```

or (if you are in `src`):

```bash
javac com/example/bank/*.java
```

#### Running:

From the **project root** (where `src` is present):

```bash
java com.example.bank.BankMain
```

`Java` uses the **fully qualified class name** that includes the package.

Example `BankMain`:

```java
// File: com/example/bank/BankMain.java

package com.example.bank;

public class BankMain {
    public static void main(String[] args) {
        Account acc = new Account(1000);
        acc.deposit(500);
        System.out.println("Balance: " + acc.getBalance());
    }
}
```

---

## 4. Importing Classes from Packages

You can **reuse classes from other packages** using `import`.

### 4.1 Importing a Single Class

```java
import java.util.Scanner;

public class InputDemo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter a number: ");
        int num = sc.nextInt();
        System.out.println("You entered: " + num);
        sc.close();
    }
}
```

Here, `java.util.Scanner` is imported from the `java.util` package.

### 4.2 Importing All Classes in a Package

Use `*` to import all public classes and interfaces from a package:

```java
import java.util.*;

public class ListDemo {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("Apple");
        list.add("Banana");
        System.out.println(list);
    }
}
```

Important:
- `*` does **not** import sub‑packages.
- Only **public** members of the package are available.

### 4.3 Static Imports

Static import allows importing **static members** (methods, constants) directly.

```java
import static java.lang.Math.*;
import static java.lang.System.*;

public class StaticImportDemo {
    public static void main(String[] args) {
        double x = 16.0;
        out.println("sqrt(16) = " + sqrt(x));   // no Math.sqrt
    }
}
```

Use static import when:
- You frequently use constants from a class (e.g., `Math.PI`).
- You want cleaner, more readable code.

---

## 5. Access Modifiers in Java

Access modifiers control **where** a class, method, or field can be accessed.

Java supports four access levels:

- `public`
- `protected`
- `default` (no keyword, also called **package‑private**)
- `private`

### 5.1 Overview of Access Modifiers

| Modifier   | Same Class | Same Package | Subclass (any package) | Other Packages |
|-----------|-----------|--------------|------------------------|----------------|
| `private` | ✅        | ❌           | ❌                     | ❌             |
| *default* | ✅        | ✅           | ❌                     | ❌             |
| `protected`| ✅       | ✅           | ✅ (if subclass)       | ❌             |
| `public`  | ✅        | ✅           | ✅                     | ✅             |

More explanation below.

### 5.2 public

`public` – **most visible** access level.

- Can be accessed **from anywhere**.
- Class, method, or field is **not restricted** by package boundaries.

Example:

```java
// File: com.example.bank.Account.java

package com.example.bank;

public class Account {
    public double balance;   // public field

    public void deposit(double amount) {
        balance += amount;
    }
}
```

From any other package:

```java
// Different package
package com.example.test;

import com.example.bank.Account;

public class TestPublicAccess {
    public static void main(String[] args) {
        Account acc = new Account();
        acc.balance = 1000;          // allowed
        acc.deposit(500);            // allowed
    }
}
```

### 5.3 private

`private` – **most restricted** access level.

- Accessible **only within the same class**.
- Used mainly for **data hiding** and **encapsulation**.

Example:

```java
// File: com.example.bank.Account.java

package com.example.bank;

public class Account {
    private double balance;

    public Account(double initialBalance) {
        this.balance = initialBalance;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
}
```

From another class:

```java
// com.example.test.AccountTest

package com.example.test;

import com.example.bank.Account;

public class AccountTest {
    public static void main(String[] args) {
        Account acc = new Account(1000);

        // acc.balance = 2000;   // ❌ COMPILE ERROR – private

        System.out.println(acc.getBalance());  // ✅ OK
    }
}
```

### 5.4 protected

`protected` – accessible in:

- Same class.
- Same package.
- Subclasses in **any package** (even outside the original package).

Typically used for **inheritance**‑related members.

Example:

```java
// File: com.example.parent.Parent.java

package com.example.parent;

public class Parent {
    protected int age;

    protected void display() {
        System.out.println("Parent age: " + age);
    }
}
```

Subclass in a **different package**:

```java
// File: com.example.child.Child.java

package com.example.child;

import com.example.parent.Parent;

public class Child extends Parent {
    public void showAge() {
        age = 25;            // ✅ OK – protected
        display();           // ✅ OK – protected
    }
}
```

From a **non‑subclass** class outside the package:

```java
// File: com.example.other.OtherClass.java

package com.example.other;

import com.example.parent.Parent;

public class OtherClass {
    public static void main(String[] args) {
        Parent p = new Parent();

        // p.age = 30;        // ❌ COMPILE ERROR – not accessible
        // p.display();       // ❌ COMPILE ERROR – not accessible
    }
}
```

### 5.5 default (package‑private)

If **no access modifier** is specified, it is **default** (package‑private).

Rules:
- Accessible **only within the same package**.
- Not accessible from other packages, even for subclasses.

Example:

```java
// File: com.example.bank.Helper.java

package com.example.bank;

class Helper {   // default access
    void helperMethod() {
        System.out.println("Helper method");
    }
}
```

Another class **in the same package**:

```java
// File: com.example.bank.Account.java

package com.example.bank;

class Account {
    void testDefault() {
        Helper h = new Helper();
        h.helperMethod();   // ✅ OK – same package
    }
}
```

From a **different package**:

```java
// File: com.example.test.TestDefault.java

package com.example.test;

import com.example.bank.Helper;  // ❌ Not allowed

public class TestDefault {
    public static void main(String[] args) {
        // Cannot use Helper here
    }
}
```

---

## 6. Access Modifiers – Detailed Table

| Access Modifier | Same Class | Same Package | Subclass (any package) | Other Packages (non‑subclass) | Notes |
|-----------------|-----------|--------------|------------------------|-------------------------------|-------|
| `private`       | ✅        | ❌           | ❌                     | ❌                            | Only inside the class |
| *default*       | ✅        | ✅           | ❌                     | ❌                            | Only within the package |
| `protected`     | ✅        | ✅           | ✅                     | ❌                            | Also accessible to subclasses anywhere |
| `public`        | ✅        | ✅           | ✅                     | ✅                            | Accessible everywhere |

---

## 7. Usage Examples of Access Modifiers

### 7.1 public usage

Use `public` for:
- **Main API classes** that other packages need to use.
- **Public methods** that form the interface of a class.

Example:

```java
package com.example.bank;

public class BankService {
    public void transfer(Account from, Account to, double amount) {
        // ... logic
    }
}
```

This class can be used from any other package.

### 7.2 private usage

Use `private` for:
- **Helper methods** or **inner variables** not meant to be exposed.
- **Data hiding** in encapsulation.

Example:

```java
public class Calculator {
    private double tempResult;

    private double doSquare(double x) {
        return x * x;
    }

    public double square(double x) {
        tempResult = doSquare(x);
        return tempResult;
    }
}
```

End users should only call `square()`, not `doSquare()` or access `tempResult`.

### 7.3 protected usage

Use `protected` for:
- **Methods or fields** that should be available to subclasses but not to unrelated classes.
- **Template method pattern** or inheritance‑based frameworks.

Example:

```java
package com.example.vehicle;

public abstract class Vehicle {
    protected String brand;

    protected void startEngine() {
        System.out.println("Engine started");
    }
}

package com.example.car;

import com.example.vehicle.Vehicle;

public class Car extends Vehicle {
    public void startCar() {
        brand = "Toyota";           // ✅ OK
        startEngine();              // ✅ OK
    }
}
```

### 7.4 default access usage

Use **default** when:
- You want **package‑local** helpers.
- You design an **internal API** inside a module.

Example:

```java
// File: com.example.internal.InternalUtil.java

package com.example.internal;

class InternalUtil {   // default
    static void logInternal(String msg) {
        System.out.println("[INTERNAL] " + msg);
    }
}
```

Only classes in `com.example.internal` can use `InternalUtil`.

---

## 8. Best Practices for Packages and Access Modifiers

- **Use packages** to logically group related classes (e.g., `com.example.user`, `com.example.payment`).
- Use **camel‑case for classes** and **lower‑case for packages**.
- Prefer **specific access** – make fields `private` and expose via `public` methods.
- Use `protected` only when you intend **inheritance**; avoid over‑using it.
- Use **default (package‑private)** for helper classes that should not be exposed to other modules.
- Avoid `public` for everything; design a **clear public API** and keep internals hidden.
- Use **well‑named packages** like `com.company.project.module`.

---

## 9. Common Interview‑Style Questions

1. **Difference between `default` and `protected`?**  
   - `default`: Only accessible in the same package.  
   - `protected`: Accessible in the same package and by subclasses even in other packages.

2. **Can a `private` method be overridden?**  
   - No. `private` methods are **not inherited**, so they cannot be overridden. They can be **hidden** in subclasses but not overridden.

3. **Can a class be `private`?**  
   - A **top‑level class** cannot be `private`.  
   - Only **inner classes** can be `private`.

4. **What is the default access modifier for a class?**  
   - If no modifier is written, the class has **default** (package‑private) access.

5. **Why use packages?**  
   - To avoid name clashes, organize code, and control access between modules.

6. **Why is `main()` method `public static void`?**  
   - `public`: So JVM can call it from outside.  
   - `static`: So JVM can call it without creating an object.  
   - `void`: No return value.

---
