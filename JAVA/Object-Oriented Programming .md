# Object-Oriented Programming 

### Methods in Java
1. [Introduction to Methods](#introduction-to-methods)
2. [Method Creation](#method-creation)
3. [Method Calling](#method-calling)
4. [Parameters and Arguments](#parameters-and-arguments)
5. [Return Types](#return-types)
6. [Method Signature](#method-signature)
7. [Method Overloading](#method-overloading)
8. [Rules and Best Practices](#rules-and-best-practices)
9. [Examples](#examples)
10. [Quick Revision](#quick-revision)

---
### Object-Oriented Programming (OOP) Principles

1. [Introduction to OOP](#introduction-to-oop)
2. [Encapsulation](#encapsulation)
3. [Inheritance](#inheritance)
4. [Polymorphism](#polymorphism)
   - [Compile-time Polymorphism](#compile-time-polymorphism)
   - [Runtime Polymorphism](#runtime-polymorphism)
5. [Abstraction](#abstraction)
6. [Differences Between OOP Principles](#differences-between-oop-principles)
7. [Advantages of OOP](#advantages-of-oop)
8. [Important Exam Points](#important-exam-points)
9. [Examples](#examples)
10. [Quick Revision](#quick-revision)

### Advanced OOP Concepts in Java

1. [Introduction](#introduction)
2. [The `this` Keyword](#the-this-keyword)
3. [The `super` Keyword](#the-super-keyword)
4. [Method Overriding](#method-overriding)
5. [Abstract Classes](#abstract-classes)
6. [Interfaces](#interfaces)
7. [Abstract Class vs Interface](#abstract-class-vs-interface)
8. [Key Differences](#key-differences)
9. [Examples](#examples)
10. [Quick Revision](#quick-revision)
## Introduction to Methods

A **method** is a block of code that performs a specific task. Methods help break a program into smaller, reusable parts, making code easier to read, debug, and maintain.

In Java, methods are used to:
- Reuse code.
- Improve readability.
- Organize logic into small units.
- Avoid repetition.

![Java method declaration diagram](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/4384ae3ebb571caec929ac6ed0b6825b8c9bda39.jpg)

---

## Method Creation

A method is created by writing its declaration and body inside a class.

### Basic Syntax

```java
accessModifier returnType methodName(parameterList) {
    // method body
}
```

### Parts of a Method
- **Access modifier**: Defines visibility such as `public`, `private`, or `protected`.
- **Return type**: Type of value the method returns.
- **Method name**: Name used to call the method.
- **Parameter list**: Inputs accepted by the method.
- **Method body**: Code executed when the method is called.

### Example

```java
class Demo {
    void greet() {
        System.out.println("Hello!");
    }
}
```

Here:
- `void` means the method does not return a value.
- `greet` is the method name.
- `()` means it takes no parameters.

---

## Method Calling

A method must be called to execute its code.

### Syntax

```java
methodName();
```

If the method requires parameters, values must be passed during the call.

### Example

```java
class Demo {
    void greet() {
        System.out.println("Hello!");
    }

    public static void main(String[] args) {
        Demo obj = new Demo();
        obj.greet();
    }
}
```

### Output
```java
Hello!
```

![Method call sequence diagram](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/30888edbbbb87724ceef28363e6396883554c139.jpg)

---

## Parameters and Arguments

Parameters and arguments are closely related but not the same.

### Parameters
Parameters are variables defined in the method declaration.

### Arguments
Arguments are the actual values passed when the method is called.

### Example

```java
class Demo {
    void add(int a, int b) {
        System.out.println(a + b);
    }

    public static void main(String[] args) {
        Demo obj = new Demo();
        obj.add(10, 20);
    }
}
```

In this example:
- `int a, int b` are **parameters**
- `10, 20` are **arguments**

### Types of Parameters
- **No parameter method**
- **Single parameter method**
- **Multiple parameter method**

### Example with multiple parameters

```java
void displayInfo(String name, int age) {
    System.out.println(name + " is " + age + " years old.");
}
```

![Java parameters and return type flowchart](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/fabfd9c95a8b40234a9ac05803016536b61da4a9.jpg)

---

## Return Types

The return type tells what kind of value a method sends back after execution.

### Common Return Types
- `int`
- `double`
- `char`
- `boolean`
- `String`
- user-defined class types
- `void` if nothing is returned

### Example with return value

```java
class Demo {
    int sum(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        Demo obj = new Demo();
        int result = obj.sum(5, 7);
        System.out.println(result);
    }
}
```

### Output
```java
12
```

### Important Points
- If return type is not `void`, the method must return a value of that type.
- `return` ends the method immediately.
- A method with `void` does not return any value.

---

## Method Signature

A method signature is used to identify a method.

### It includes:
- Method name
- Number of parameters
- Type of parameters
- Order of parameters

### Example

```java
add(int, int)
add(double, double)
add(int, int, int)
```

These are different signatures because the parameter lists differ.

### Note
In Java, return type alone is **not** part of the method signature for overloading.

---

## Method Overloading

Method overloading means having multiple methods with the **same name** in the same class but with **different parameter lists**.

### Rules for Overloading
- Same method name.
- Different number of parameters, or
- Different parameter types, or
- Different order of parameter types.

### Example

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```

### Why Overloading is Useful
- Makes code easier to read.
- Supports the same operation with different inputs.
- Reduces method name confusion.

### Invalid Overloading Example

```java
class Test {
    int show(int a) {
        return a;
    }

    double show(int a) {
        return a;
    }
}
```

This is invalid because only the return type is different.

![Method overloading illustration](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/4759db297f2e109e7fb6e3c3f54703a9aa033116.jpg)

---

## Rules and Best Practices

- Choose meaningful method names.
- Keep methods small and focused.
- Use parameters only when needed.
- Return a value only when the caller needs it.
- Use overloading when the same action works for different input types.
- Do not overload methods by changing only the return type.

### Best Practice Example
Use `area(int side)` and `area(int length, int breadth)` instead of completely unrelated names if both calculate area.

---

## Examples

### 1. Method without parameters

```java
class Demo {
    void printMessage() {
        System.out.println("Welcome to Java");
    }

    public static void main(String[] args) {
        Demo obj = new Demo();
        obj.printMessage();
    }
}
```

### 2. Method with parameters and return type

```java
class Demo {
    int multiply(int a, int b) {
        return a * b;
    }

    public static void main(String[] args) {
        Demo obj = new Demo();
        System.out.println(obj.multiply(4, 5));
    }
}
```

### 3. Overloaded methods

```java
class Display {
    void show(int a) {
        System.out.println("Integer: " + a);
    }

    void show(String s) {
        System.out.println("String: " + s);
    }

    void show(int a, int b) {
        System.out.println("Sum: " + (a + b));
    }
}
```

---

## Quick Revision

### Method Creation
- Define inside a class.
- Include return type, name, parameters, and body.

### Method Calling
- Use method name with parentheses.
- Pass arguments if required.

### Parameters and Arguments
- Parameters are in the declaration.
- Arguments are values passed in the call.

### Return Types
- Tell what the method sends back.
- Use `void` if nothing is returned.

### Method Overloading
- Same name, different parameter list.
- Return type alone cannot overload a method.

---

## Short Notes

- A method is reusable code that performs a task.
- Method creation means defining the method.
- Method calling means executing the method.
- Parameters are inputs written in method definition.
- Arguments are actual values passed at runtime.
- Return type defines the output type.
- Overloading allows same method name with different parameter lists.

---

## Revision Example

```java
class Example {
    void show() {
        System.out.println("No parameters");
    }

    void show(int a) {
        System.out.println("One parameter: " + a);
    }

    int show(int a, int b) {
        return a + b;
    }
}
```

This class shows:
- method creation,
- method calling,
- parameters,
- return type,
- method overloading.

---

## Introduction to OOP

Object-Oriented Programming is a programming style based on **objects** and **classes**. It helps organize code in a way that resembles real-world entities.

An object contains:
- Data, also called attributes or fields.
- Behavior, also called methods.

A class is a blueprint for creating objects.

### Core OOP Principles
- Encapsulation
- Inheritance
- Polymorphism
- Abstraction

These are often called the four pillars of OOP.

![OOP pillars diagram](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/c38afd89c571f8f2fad839d3e0250a6edaeb1def.jpg)

---

## Encapsulation

Encapsulation means wrapping data and methods into a single unit, usually a class, and controlling access to the data.

In Java, encapsulation is achieved using:
- `private` data members.
- `public` getter and setter methods.

### Why Encapsulation is Important
- Protects data from direct access.
- Improves security.
- Makes code easier to maintain.
- Helps control how values are changed.

### Example

```java
class Student {
    private String name;
    private int age;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setAge(int age) {
        if(age > 0) {
            this.age = age;
        }
    }

    public int getAge() {
        return age;
    }
}
```

### Real-Life Idea
A capsule protects the medicine inside it. Similarly, encapsulation protects data inside a class.

![Encapsulation in Java](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/c139c55022f3bc7e504a9fedf9719f9df432ac9c.jpg)

---

## Inheritance

Inheritance allows one class to acquire properties and methods of another class.

The existing class is called the **parent class** or **superclass**.  
The new class is called the **child class** or **subclass**.

### Syntax

```java
class Child extends Parent {
}
```

### Why Inheritance is Useful
- Supports code reuse.
- Reduces duplication.
- Makes programs easier to extend.
- Helps create hierarchical relationships.

### Example

```java
class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking...");
    }
}
```

### Types of Inheritance in Java
- Single inheritance
- Multilevel inheritance
- Hierarchical inheritance

Java does not support multiple inheritance with classes directly.

![Inheritance diagram](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/f2e3dee0b47423b7667775b6a3853d0abb275e21.jpg)

---

## Polymorphism

Polymorphism means **many forms**. It allows one method or object to behave differently in different situations.

In Java, polymorphism is mainly of two types:
- Compile-time polymorphism
- Runtime polymorphism

![Polymorphism diagram](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/20755b39b1044fe8ce0277ba0c385007f4467d14.jpg)

---

## Compile-time Polymorphism

Compile-time polymorphism is achieved using **method overloading**.

The method to be called is decided by the compiler at compile time.

### Method Overloading Rules
- Same method name.
- Different number of parameters, or
- Different types of parameters, or
- Different order of parameters.

### Example

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```

### Key Points
- Also called static polymorphism.
- Also called early binding.

### Example Use
A calculator can add two integers, three integers, or two decimal numbers using the same method name.

---

## Runtime Polymorphism

Runtime polymorphism is achieved using **method overriding**.

The method to be called is decided at runtime based on the actual object.

### Method Overriding Rules
- Same method name.
- Same parameter list.
- Child class provides a new implementation.
- It happens in inheritance.

### Example

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}
```

### Key Points
- Also called dynamic polymorphism.
- Also called late binding.

### Example Use
If an `Animal` reference points to a `Dog` object, the `Dog` version of the method runs.

---

## Abstraction

Abstraction means hiding internal implementation details and showing only the essential features.

It helps users focus on **what** an object does, not **how** it does it.

### How Abstraction is Achieved in Java
- Abstract classes
- Interfaces

### Example with Abstract Class

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

### Why Abstraction is Important
- Reduces complexity.
- Improves clarity.
- Helps in code reuse.
- Supports modular design.

![Abstraction and encapsulation diagram](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/b5a319296a593c366c000a11b5625045c47703e3.jpg)

---

## Differences Between OOP Principles

| Concept | Meaning | Main Purpose | Java Mechanism |
|---|---|---|---|
| Encapsulation | Wrapping data and methods together | Data protection | private fields, getters, setters |
| Inheritance | One class acquires properties of another | Code reuse | extends |
| Polymorphism | One thing behaves in many forms | Flexibility | overloading, overriding |
| Abstraction | Hiding details and showing essentials | Simplicity | abstract class, interface |

---

## Advantages of OOP

- Code reusability.
- Better security with data hiding.
- Easier maintenance.
- More flexibility.
- Easier debugging and testing.
- Better real-world modeling.

---

## Important Exam Points

- Encapsulation = data hiding + controlled access.
- Inheritance = child class gets features of parent class.
- Polymorphism = same name, different behavior.
- Compile-time polymorphism = method overloading.
- Runtime polymorphism = method overriding.
- Abstraction = hide implementation, show functionality.
- Java does not support multiple inheritance with classes.

---

## Examples

### Encapsulation Example

```java
class BankAccount {
    private double balance;

    public void setBalance(double balance) {
        if(balance >= 0) {
            this.balance = balance;
        }
    }

    public double getBalance() {
        return balance;
    }
}
```

### Inheritance Example

```java
class Vehicle {
    void start() {
        System.out.println("Vehicle starts");
    }
}

class Car extends Vehicle {
    void drive() {
        System.out.println("Car drives");
    }
}
```

### Polymorphism Example

```java
class MathOp {
    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

### Abstraction Example

```java
abstract class Payment {
    abstract void pay();
}

class UPI extends Payment {
    void pay() {
        System.out.println("Paid using UPI");
    }
}
```

---

## Quick Revision

### Encapsulation
- Protects data.
- Uses private variables and public methods.

### Inheritance
- Reuses code from parent to child.
- Uses `extends`.

### Polymorphism
- Same method name, different behavior.
- Overloading = compile-time.
- Overriding = runtime.

### Abstraction
- Hides implementation.
- Shows essential features only.

---

## Summary Example

```java
abstract class Animal {
    private String name;

    Animal(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    abstract void sound();
}

class Cat extends Animal {
    Cat(String name) {
        super(name);
    }

    void sound() {
        System.out.println(getName() + " says Meow");
    }
}
```

This example shows:
- Encapsulation through private data.
- Inheritance through `extends`.
- Abstraction through abstract class.
- Polymorphism through method overriding.




---

## Introduction

Advanced OOP concepts help build flexible, reusable, and maintainable Java programs. These concepts are widely used in inheritance, polymorphism, and abstraction. Understanding them is essential for both exams and real-world development.

---

## The `this` Keyword

The `this` keyword refers to the current object of the class. It is mainly used to resolve naming conflicts between instance variables and parameters. It can also be used to call another constructor in the same class.

### Uses of `this`
- Refers to the current object.
- Accesses current class fields and methods.
- Resolves ambiguity between fields and parameters.
- Calls another constructor using `this()`.

### Example
```java
class Student {
    int id;
    String name;

    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }

    void display() {
        System.out.println(id + " " + name);
    }
}
```

### Note
`this` always points to the current object inside the class.

![this keyword in Java](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/2218696c56b4f3f4540fe9f214a82b31b4d07ec1.jpg)

---

## The `super` Keyword

The `super` keyword refers to the immediate parent class object. It is used to access parent class members and to call parent class constructors.

### Uses of `super`
- Access parent class variables.
- Call parent class methods.
- Call parent class constructor using `super()`.

### Example
```java
class Animal {
    String color = "Brown";

    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {
    String color = "Black";

    void show() {
        System.out.println(super.color);
        super.eat();
    }
}
```

### Note
`super` is useful when the child class has the same variable or method name as the parent class.

![super keyword in Java](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/bba42f06a162683ed2c30c41df34d0a80b3c7be6.jpg)

---

## Method Overriding

Method overriding occurs when a child class provides its own version of a method already defined in the parent class. It is an example of runtime polymorphism.

### Rules of Overriding
- Same method name.
- Same parameter list.
- Same or compatible return type.
- Child class method cannot reduce visibility.
- Must involve inheritance.

### Example
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

### Why It Is Important
- Supports dynamic method dispatch.
- Allows child classes to customize parent behavior.
- Improves flexibility in object-oriented design.

---

## Abstract Classes

An abstract class is a class that cannot be instantiated directly. It may contain abstract methods and concrete methods. It is used when classes share common behavior, but some details must be defined by subclasses.

### Features
- Declared using `abstract`.
- Can have fields, constructors, abstract methods, and regular methods.
- Cannot create objects directly.

### Example
```java
abstract class Shape {
    abstract void draw();

    void info() {
        System.out.println("This is a shape");
    }
}

class Circle extends Shape {
    void draw() {
        System.out.println("Drawing Circle");
    }
}
```

### Use Case
Use abstract classes when related classes share common code and structure.

![abstract class diagram](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/87a9d082c96479a91a51187d9ddbf2961e0b0570.jpg)

---

## Interfaces

An interface is a blueprint that defines a contract for classes. A class implements an interface and provides the method definitions.

### Features
- Declared using `interface`.
- Methods are abstract by default, except `default` and `static` methods.
- Variables are `public static final` by default.
- A class can implement multiple interfaces.

### Example
```java
interface Printable {
    void print();
}

class Document implements Printable {
    public void print() {
        System.out.println("Printing document");
    }
}
```

### Why Interfaces Are Used
- To achieve full abstraction.
- To support multiple inheritance of type.
- To define common behavior across unrelated classes.

![interfaces and abstract classes diagram](https://pplx-res.cloudinary.com/image/upload/pplx_search_images/14760b86c04612e7e43b0c98e42304cdd3878f77.jpg)

---

## Abstract Class vs Interface

| Feature | Abstract Class | Interface |
|---|---|---|
| Keyword | `abstract class` | `interface` |
| Methods | Abstract and concrete methods | Abstract, default, and static methods |
| Variables | Can have instance variables | Variables are public static final |
| Constructor | Allowed | Not allowed |
| Inheritance | A class can extend only one abstract class | A class can implement multiple interfaces |
| Purpose | Partial abstraction | Full abstraction and contract |

---

## Key Differences

### `this` vs `super`
- `this` refers to the current object.
- `super` refers to the parent class object.

### Overriding vs Overloading
- Overriding uses same method signature in child class.
- Overloading uses same method name with different parameters.

### Abstract Class vs Interface
- Abstract class is used for shared base behavior.
- Interface is used for defining a contract.

---

## Examples

### Example of `this`
```java
class Car {
    String brand;

    Car(String brand) {
        this.brand = brand;
    }
}
```

### Example of `super`
```java
class Parent {
    void show() {
        System.out.println("Parent");
    }
}

class Child extends Parent {
    void show() {
        super.show();
        System.out.println("Child");
    }
}
```

### Example of overriding
```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("Meow");
    }
}
```

### Example of abstract class
```java
abstract class Vehicle {
    abstract void start();
}

class Bike extends Vehicle {
    void start() {
        System.out.println("Bike starts");
    }
}
```

### Example of interface
```java
interface Flyable {
    void fly();
}

class Bird implements Flyable {
    public void fly() {
        System.out.println("Bird is flying");
    }
}
```

---

## Quick Revision

- `this` = current object.
- `super` = parent class object.
- Overriding = child class redefines parent method.
- Abstract class = partial abstraction.
- Interface = complete abstraction contract.

---

## Practice Questions

1. What is the purpose of `this` keyword?
2. What is the difference between `this` and `super`?
3. What is method overriding?
4. Why are abstract classes used?
5. Why are interfaces important in Java?
6. Can a class implement multiple interfaces?

---

## Final Example

```java
abstract class Animal {
    String name;

    Animal(String name) {
        this.name = name;
    }

    abstract void sound();
}

class Dog extends Animal {
    Dog(String name) {
        super(name);
    }

    void sound() {
        System.out.println(name + " says Bark");
    }
}
```

This single example shows:
- `this` in constructor,
- `super` in child constructor,
- abstraction using abstract class,
- overriding using child method implementation.
