# 🔹 Exception Handling in Java – Detailed Notes

## Table of Contents

- [1. What is an Exception?](#1-what-is-an-exception)
- [2. Types of Exceptions](#2-types-of-exceptions)
- [3. Exception Hierarchy](#3-exception-hierarchy)
- [4. try, catch, finally](#4-try-catch-finally)
  - [4.1. try block](#41-try-block)
  - [4.2. catch block](#42-catch-block)
  - [4.3. finally block](#43-finally-block)
  - [4.4. Execution flow examples](#44-execution-flow-examples)
- [5. Multiple catch blocks](#5-multiple-catch-blocks)
- [6. try‑with‑resources](#6-trywithresources)
- [7. throw vs throws](#7-throw-vs-throws)
  - [7.1. throw keyword](#71-throw-keyword)
  - [7.2. throws keyword](#72-throws-keyword)
- [8. Custom (User‑Defined) Exceptions](#8-custom-user-defined-exceptions)
  - [8.1. Creating a custom checked exception](#81-creating-a-custom-checked-exception)
  - [8.2. Creating a custom unchecked exception](#82-creating-a-custom-unchecked-exception)
- [9. Best Practices in Exception Handling](#9-best-practices-in-exception-handling)
- [10. Common Examples and Use Cases](#10-common-examples-and-use-cases)

---

## 1. What is an Exception?

An **exception** is an **unexpected or abnormal event** that occurs during the execution of a program and **disturbs the normal flow** of the application.

Java provides a built‑in **exception handling mechanism** to gracefully handle such situations instead of abruptly terminating the program.

### Key points:
- Exceptions occur at **runtime** (not at compile‑time).
- Java places exceptions into an **object** of a class derived from `Throwable`.
- Exception objects can be **caught and handled** using `try`, `catch`, and `finally` blocks.

---

## 2. Types of Exceptions

### 2.1 Checked Exceptions
- Known at **compile time**.
- Must be either **handled** (using `try‑catch`) or **declared** using `throws`.
- Examples: `IOException`, `SQLException`, `FileNotFoundException`.

### 2.2 Unchecked Exceptions
- Occur at **runtime**.
- Not checked by the compiler.
- Subclasses of `RuntimeException` and `Error`.
- Examples: `NullPointerException`, `ArrayIndexOutOfBoundsException`, `ArithmeticException`.

### 2.3 Errors
- Serious problems that an application should **not try to handle**.
- Subclasses of `Error` (e.g., `OutOfMemoryError`, `StackOverflowError`).

---

## 3. Exception Hierarchy

All exceptions and errors are subclasses of the base class `java.lang.Throwable`.

Simplified hierarchy:

- `Throwable`
  - `Error` (e.g., `OutOfMemoryError`)
  - `Exception`
    - **Checked Exceptions** (e.g., `IOException`)
    - **RuntimeException** → **Unchecked Exceptions** (e.g., `NullPointerException`)

Java’s `Exception` class is the base for most application‑level exceptions.

---

## 4. try, catch, finally

### 4.1 try block

The `try` block encloses the code that **might throw an exception**.

```java
try {
    // risky code that may throw an exception
    int result = 10 / 0; // this may throw ArithmeticException
}
```

Rules:
- A `try` block **must** be followed by at least one `catch` or `finally`.
- You cannot use `try` alone.

---

### 4.2 catch block

The `catch` block **handles** the exception thrown inside the `try` block.

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero: " + e.getMessage());
}
```

Key points:
- `catch` always follows a `try`.
- Each `catch` block can handle **one specific exception type** (or a superclass).
- The parameter `e` is an exception object providing details like message and stack trace.

---

### 4.3 finally block

The `finally` block is **always executed**, regardless of whether an exception occurred or not.

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Division error");
} finally {
    System.out.println("Finally block runs always");
}
```

Use cases for `finally`:
- Closing files, database connections, network sockets.
- Releasing resources and doing cleanup.

When `finally` is **not executed**:
- If the JVM exits (e.g., `System.exit(0)`).
- If the thread dies abruptly (e.g., due to a fatal error).

---

### 4.4 Execution flow examples

#### Case 1: No exception

```java
try {
    System.out.println("Inside try – no exception");
} catch (Exception e) {
    System.out.println("Catch block");
} finally {
    System.out.println("Finally block");
}
```
```
Output:
Inside try – no exception
Finally block
```

#### Case 2: Exception thrown and caught

```java
try {
    int x = 10 / 0;
    System.out.println("After division");
} catch (ArithmeticException e) {
    System.out.println("Caught: " + e.getMessage());
} finally {
    System.out.println("Finally block");
}
```
```
Output:
Caught: / by zero
Finally block
```


#### Case 3: Exception not caught (no matching catch)

```java
try {
    int x = 10 / 0;
} catch (NullPointerException e) {
    System.out.println("This will not execute");
} finally {
    System.out.println("Finally executes");
}

// After finally, uncaught ArithmeticException terminates the program flow.
```

---

## 5. Multiple catch blocks

You can have **multiple catch blocks** to handle different exception types.

```java
try {
    // risky code
    int a = Integer.parseInt("abc");
    int b = 10 / 0;
} catch (NumberFormatException e) {
    System.out.println("Invalid number format");
} catch (ArithmeticException e) {
    System.out.println("Division by zero");
} catch (Exception e) {
    System.out.println("Some other exception: " + e.getMessage());
} finally {
    System.out.println("Finally block");
}
```

Rules:
- Catch blocks must be ordered from **most specific to most general**.
- If you place a generic `Exception` handler **before** specific ones, it will **catch everything** and the later catch blocks are unreachable.

Starting from **Java 7+**, you can also use **multi‑catch** for the same handler:

```java
try {
    // risky code
} catch (ArithmeticException | NumberFormatException e) {
    System.out.println("Handled by multi‑catch: " + e.getMessage());
}
```

---

## 6. try‑with‑resources

Java 7+ introduced **try‑with‑resources** for **automatic resource management**.

Any resource that implements `java.lang.AutoCloseable` (e.g., `InputStream`, `Writer`, `Connection`) can be used here.

```java
try (FileReader reader = new FileReader("data.txt")) {
    // use the reader
    int ch;
    while ((ch = reader.read()) != -1) {
        System.out.print((char) ch);
    }
} catch (IOException e) {
    System.out.println("I/O error: " + e.getMessage());
}
// reader is automatically closed even if exception occurs
```

Features:
- Resources declared in the parentheses are **automatically closed**.
- No need to write `finally` for closing resources.
- More readable and less error‑prone.

---

## 7. throw vs throws

### 7.1 throw keyword

`throw` is used **inside a method** to **explicitly throw** an exception.

```java
public void checkAge(int age) {
    if (age < 0) {
        throw new IllegalArgumentException("Age cannot be negative");
    }
    System.out.println("Valid age: " + age);
}
```

Use it:
- To manually throw checked or unchecked exceptions.
- To enforce business rules or validations.

The syntax:
```java
throw new ExceptionClass("Message");
```

---

### 7.2 throws keyword

`throws` is used in the **method signature** to **declare** that the method **may throw** one or more exceptions.

```java
public void readFile(String filename) throws IOException {
    FileReader reader = new FileReader(filename);
    // ... read operations
}
```

Client code must either:
- Handle it with `try‑catch`, or
- Declare it again with `throws`.

Example of declaration with multiple exceptions:

```java
public void processData(String file, int id)
        throws IOException, SQLException {
    // ...
}
```

Key differences:

| Feature              | `throw`                                      | `throws`                                      |
|----------------------|----------------------------------------------|-----------------------------------------------|
| Where used           | Inside a method body                         | In method signature                           |
| Purpose              | To **throw** an exception manually           | To **declare** exceptions that may occur      |
| Affects only one     | Can throw **one** exception at a time        | Can declare **multiple** exceptions           |
| Mandatory for checked| No (only for logic)                          | Yes (for checked exceptions)                  |

---

## 8. Custom (User‑Defined) Exceptions

Java allows you to create **your own exception classes** for specific business scenarios.

### 8.1 Creating a custom checked exception

To create a **checked exception**, extend `Exception` (not `RuntimeException`).

```java
// Custom checked exception
class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message);
    }
}

class BankAccount {
    private double balance;

    public BankAccount(double initialBalance) {
        this.balance = initialBalance;
    }

    public void withdraw(double amount) throws InsufficientFundsException {
        if (amount > balance) {
            throw new InsufficientFundsException(
                    "Cannot withdraw " + amount + ", available balance: " + balance
            );
        }
        balance -= amount;
        System.out.println("Withdrawn: " + amount + ", Remaining: " + balance);
    }
}

public class CustomExceptionDemo {
    public static void main(String[] args) {
        BankAccount account = new BankAccount(500.0);

        try {
            account.withdraw(600.0);
        } catch (InsufficientFundsException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```
```
Output:
Error: Cannot withdraw 600.0, available balance: 500.0
```

### 8.2 Creating a custom unchecked exception

To create an **unchecked exception**, extend `RuntimeException`.

```java
// Custom unchecked exception
class InvalidEmailException extends RuntimeException {
    public InvalidEmailException(String message) {
        super(message);
    }
}

class User {
    private String email;

    public User(String email) {
        if (!email.contains("@")) {
            throw new InvalidEmailException("Invalid email format: " + email);
        }
        this.email = email;
    }

    public void display() {
        System.out.println("User email: " + email);
    }
}

public class UncheckedCustomExceptionDemo {
    public static void main(String[] args) {
        try {
            User u1 = new User("john.example.com"); // invalid
        } catch (InvalidEmailException e) {
            System.out.println("Caught: " + e.getMessage());
        }

        User u2 = new User("john@example.com"); // valid
        u2.display();
    }
}
```
```
Output:
Caught: Invalid email format: john.example.com
User email: john@example.com
```

---

## 9. Best Practices in Exception Handling

- **Use specific exceptions** instead of generic `Exception`.
- **Don’t ignore caught exceptions**; log or take action.
- **Use checked exceptions** for recoverable conditions and **unchecked** for programming errors.
- **Avoid throwing generic RuntimeExceptions**; create custom exceptions for clarity.
- **Don’t catch and re‑throw without context** unless you add useful information.
- **Use try‑with‑resources** for streams, files, and connections.
- **Validate inputs early** and throw exceptions early (`fail‑fast`).
- **Document exceptions** in Javadoc using `@throws`.
- **Avoid throwing exceptions in loops** frequently; handle conditions outside the loop when possible.

---

## 10. Common Examples and Use Cases

### 10.1 Handling user input errors

```java
import java.util.Scanner;

class InputValidator {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a number: ");
        try {
            int num = Integer.parseInt(sc.nextLine());
            System.out.println("You entered: " + num);
        } catch (NumberFormatException e) {
            System.out.println("Invalid input. Please enter a valid integer.");
        } finally {
            sc.close();
        }
    }
}
```

### 10.2 File handling with checked exceptions

```java
import java.io.FileReader;
import java.io.IOException;

class FileReaderDemo {
    public static void main(String[] args) {
        try (FileReader fr = new FileReader("data.txt")) {
            int ch;
            while ((ch = fr.read()) != -1) {
                System.out.print((char) ch);
            }
        } catch (IOException e) {
            System.err.println("File error: " + e.getMessage());
        }
    }
}
```

### 10.3 Custom exception in a service layer

```java
// Business layer with custom exception
class OrderService {
    private int availableStock = 100;

    public void placeOrder(int quantity)
            throws OrderException {
        if (quantity <= 0) {
            throw new OrderException("Quantity must be positive");
        }
        if (quantity > availableStock) {
            throw new OrderException(
                    "Stock not sufficient. Available: " + availableStock
            );
        }
        availableStock -= quantity;
        System.out.println("Order placed for " + quantity + " items");
    }
}

class OrderException extends Exception {
    public OrderException(String message) {
        super(message);
    }
}

public class OrderApp {
    public static void main(String[] args) {
        OrderService service = new OrderService();

        try {
            service.placeOrder(120);
        } catch (OrderException e) {
            System.out.println("Order failed: " + e.getMessage());
        }

        try {
            service.placeOrder(20);
        } catch (OrderException e) {
            System.out.println("Order failed: " + e.getMessage());
        }
    }
}
```
```
Output:
Order failed: Stock not sufficient. Available: 100
Order placed for 20 items
```
