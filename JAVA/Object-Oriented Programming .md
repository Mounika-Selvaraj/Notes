# Java Methods Notes

## Table of Contents
### Classes & Objects
1. [Introduction to Methods](#introduction-to-methods)
2. [Method Creation](#method-creation)
3. [Calling Methods](#calling-methods)
4. [Parameters and Arguments](#parameters-and-arguments)
5. [Return Types](#return-types)
6. [Method Signature](#method-signature)
7. [Method Overloading](#method-overloading)
8. [Rules and Restrictions](#rules-and-restrictions)
9. [Examples](#examples)
10. [Quick Revision](#quick-revision)

---
### OOP Principles in Java

1. [Introduction to OOP](#introduction-to-oop)
2. [Encapsulation](#encapsulation)
3. [Inheritance](#inheritance)
4. [Polymorphism](#polymorphism)
   - [Compile-time Polymorphism](#compile-time-polymorphism)
   - [Runtime Polymorphism](#runtime-polymorphism)
5. [Abstraction](#abstraction)
6. [Differences Between the Principles](#differences-between-the-principles)
7. [Real-Life Examples](#real-life-examples)
8. [Quick Revision](#quick-revision)
## Introduction to Methods

A method is a block of code that performs a specific task. Methods help organize code, improve readability, and make programs reusable. In Java, methods are written inside classes and can be called whenever needed. [web:11]

**Why methods are useful:**
- Code reusability.
- Easier debugging.
- Better organization.
- Reduced repetition.

---

## Method Creation

A method declaration in Java usually includes:
- Access modifier.
- Return type.
- Method name.
- Parameter list.
- Method body.

The basic method structure is:

```java
accessModifier returnType methodName(parameters) {
    // body
}
```

### Example

```java
public int add(int a, int b) {
    return a + b;
}
```

### Explanation
- `public` is the access modifier.
- `int` is the return type.
- `add` is the method name.
- `(int a, int b)` are the parameters.
- `return a + b;` sends the result back. [web:11][web:3]

---

## Calling Methods

A method is called by using its name followed by parentheses. If the method has parameters, values must be passed during the call.

### Example

```java
public class Demo {
    public static void main(String[] args) {
        Demo obj = new Demo();
        int result = obj.add(5, 3);
        System.out.println(result);
    }

    public int add(int a, int b) {
        return a + b;
    }
}
```

### Output
```java
8
```

When calling a method, the arguments must match the parameters in type, number, and order. [web:6][web:12]

---

## Parameters and Arguments

Parameters are the variables listed in a method declaration. Arguments are the actual values passed when the method is called. Java allows primitive types, objects, and arrays as parameters. [web:6][web:12]

### Example

```java
public void greet(String name) {
    System.out.println("Hello, " + name);
}
```

Here:
- `name` is the parameter.
- `"Mounika"` would be the argument if called like this:

```java
greet("Mounika");
```

### Important Points
- Parameters are written in the method definition.
- Arguments are written in the method call.
- The number and order must match.
- Java passes arguments by value. [web:6][web:12]

---

## Return Types

The return type tells what kind of value a method sends back. If a method does not return anything, its return type is `void`. The value returned must match the declared return type. [web:3][web:11]

### Example with return value

```java
public int square(int n) {
    return n * n;
}
```

### Example with `void`

```java
public void displayMessage() {
    System.out.println("Welcome to Java");
}
```

### Key Points
- `int` means the method returns an integer.
- `double` means it returns a decimal value.
- `String` means it returns text.
- `void` means no value is returned. [web:3][web:11]

---

## Method Signature

In Java, the method signature includes:
- Method name.
- Parameter types in order.

It does **not** include the return type. This is important for understanding overloading. [web:11][web:26]

### Example

```java
add(int, int)
add(double, double)
add(int, int, int)
```

These are different signatures because the parameter lists differ.

---

## Method Overloading

Method overloading means having multiple methods with the same name in the same class, but with different parameter lists. It is a form of compile-time polymorphism. [web:1][web:13][web:16]

### How to overload a method
You can overload by:
- Changing the number of parameters.
- Changing the data types of parameters.
- Changing the order of parameters.

### Example 1: Different number of parameters

```java
public class MathOps {
    int sum(int a, int b) {
        return a + b;
    }

    int sum(int a, int b, int c) {
        return a + b + c;
    }
}
```

### Example 2: Different parameter types

```java
public class Printer {
    void print(int n) {
        System.out.println(n);
    }

    void print(String s) {
        System.out.println(s);
    }
}
```

### Example 3: Different order of parameters

```java
public class Demo {
    void show(int a, String b) {
        System.out.println(a + " " + b);
    }

    void show(String a, int b) {
        System.out.println(a + " " + b);
    }
}
```

Overloading helps improve readability because related actions can share the same name. [web:1][web:7]

---

## Rules and Restrictions

### Valid overloading rules
- Same method name.
- Different parameter list.
- Same class is enough for overloading.

### Not valid
- Changing only the return type is **not** overloading.
- Methods with the same name and same parameters are duplicate methods.
- Overloading is resolved at compile time, not runtime. [web:1][web:4][web:10]

### Example of invalid overloading

```java
int test() {
    return 10;
}

double test() {
    return 10.5;
}
```

This is invalid because only the return type differs. [web:4][web:7]

---

## Examples

### Complete program

```java
public class MethodNotes {

    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    void greet(String name) {
        System.out.println("Hello, " + name);
    }

    public static void main(String[] args) {
        MethodNotes obj = new MethodNotes();

        System.out.println(obj.add(10, 20));
        System.out.println(obj.add(2.5, 3.5));
        obj.greet("Mounika");
    }
}
```

### Output
```java
30
6.0
Hello, Mounika
```

This program shows:
- Method creation.
- Method calling.
- Parameters and return types.
- Method overloading. [web:1][web:3][web:11]

---

## Quick Revision

### Methods
- A method is a reusable block of code.
- It performs one task.

### Parameters and Arguments
- Parameters are in the method definition.
- Arguments are in the method call.

### Return Types
- Declared before the method name.
- `void` means no return value.

### Method Overloading
- Same method name.
- Different parameter list.
- Return type alone cannot overload a method.

### Signature
- Method name + parameter types.

---

## Diagram

[image:1]

---

## Summary Table

| Topic | Meaning | Example |
|---|---|---|
| Method creation | Defining a reusable block of code | `int add(int a, int b)` |
| Method calling | Invoking a method using its name | `obj.add(5, 3)` |
| Parameters | Variables in method definition | `int a, int b` |
| Arguments | Actual values passed to method | `5, 3` |
| Return type | Type of value returned | `int`, `double`, `void` |
| Overloading | Same name, different parameters | `sum(int, int)` and `sum(int, int, int)` |

---

## Practice Questions

1. What is the difference between parameters and arguments?
2. Why is return type not part of method overloading?
3. Write a method that returns the maximum of two numbers.
4. Create three overloaded methods named `display`.
5. What is the difference between `void` and `int` return types?


---

## Introduction to OOP

Object-Oriented Programming (OOP) is a programming style that organizes software using **objects** and **classes**. It helps build programs that are easier to manage, reuse, and extend. The four main pillars of OOP are Encapsulation, Inheritance, Polymorphism, and Abstraction. [web:30][web:33]

### Core Idea
- A **class** is a blueprint.
- An **object** is an instance of a class.
- OOP models real-world entities in code.

---

## Encapsulation

Encapsulation means wrapping data and methods into a single unit, usually a class, and restricting direct access to the data. It helps protect object state and allows controlled access through methods like getters and setters. [web:28][web:30]

### Purpose
- Protect data from unwanted access.
- Improve code maintainability.
- Provide controlled access to fields.

### How it is achieved
- Declare variables as `private`.
- Use `public` methods to access or update them.

### Example
```java
class BankAccount {
    private double balance;

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public double getBalance() {
        return balance;
    }
}
```

### Real-Life Example
An ATM hides the internal bank balance and lets you access it only through valid operations. [web:28]

---

## Inheritance

Inheritance allows one class to acquire the properties and methods of another class. It promotes code reuse and creates a parent-child relationship between classes. In Java, inheritance is commonly done using the `extends` keyword. [web:31][web:32]

### Purpose
- Reuse existing code.
- Reduce duplication.
- Create hierarchical relationships.

### Types
- Single inheritance.
- Multilevel inheritance.
- Hierarchical inheritance.

### Example
```java
class Animal {
    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking");
    }
}
```

### Explanation
- `Animal` is the parent class.
- `Dog` is the child class.
- `Dog` inherits `eat()` from `Animal`.

---

## Polymorphism

Polymorphism means “many forms.” In Java, it allows one method or interface to behave differently depending on the situation. It is one of the most powerful OOP concepts because it improves flexibility and code reuse. [web:28][web:30]

### Compile-time Polymorphism
Compile-time polymorphism is also called **method overloading**. It happens when multiple methods have the same name but different parameter lists, and the compiler decides which one to call. [web:30]

#### Example
```java
class MathOps {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```

### Runtime Polymorphism
Runtime polymorphism is also called **method overriding**. It happens when a child class provides its own version of a parent class method, and the decision is made at runtime. [web:36][web:30]

#### Example
```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Bark");
    }
}
```

### Real-Life Example
A `draw()` method may behave differently for Circle, Square, and Triangle objects. [web:28]

---

## Abstraction

Abstraction means showing only the important details and hiding the internal implementation. It helps users focus on what an object does rather than how it does it. In Java, abstraction is achieved using abstract classes and interfaces. [web:28][web:33]

### Purpose
- Hide complexity.
- Show only essential features.
- Improve modular design.

### Example using abstract class
```java
abstract class Shape {
    abstract void draw();
}

class Circle extends Shape {
    void draw() {
        System.out.println("Drawing Circle");
    }
}
```

### Real-Life Example
When you drive a car, you use the steering wheel, brake, and accelerator without knowing engine internals. [web:28]

---

## Differences Between the Principles

| Principle | Main Idea | How It Works | Example |
|---|---|---|---|
| Encapsulation | Data protection | Wrap data and methods together | Private fields with getters/setters |
| Inheritance | Code reuse | One class acquires properties of another | `Dog extends Animal` |
| Polymorphism | Many forms | Same method behaves differently | Overloading, overriding |
| Abstraction | Hide details | Show only essential features | Abstract class, interface |

---

## Real-Life Examples

### Encapsulation
A medicine capsule hides the ingredients inside and releases them in a controlled way.

### Inheritance
A child inherits traits from parents.

### Polymorphism
A single remote control works differently with a TV, AC, or sound system.

### Abstraction
A car driver uses controls without seeing all the complex mechanical parts.

---

## Quick Revision

### Encapsulation
- Hides data.
- Uses `private` fields and public methods.

### Inheritance
- Reuses existing code.
- Uses `extends`.

### Polymorphism
- One name, many forms.
- Compile-time: overloading.
- Runtime: overriding.

### Abstraction
- Hides implementation details.
- Uses abstract classes and interfaces.

---

## Diagram

[image:1]

---

## Practice Questions

1. What is the difference between encapsulation and abstraction?
2. What keyword is used for inheritance in Java?
3. What is compile-time polymorphism?
4. What is runtime polymorphism?
5. Why is encapsulation important?
6. What is the role of abstract classes?

---

## Final Note

The four pillars of OOP help make Java programs more secure, reusable, flexible, and easier to maintain. Encapsulation protects data, inheritance reuses code, polymorphism improves flexibility, and abstraction reduces complexity. [web:30][web:31][web:33]
