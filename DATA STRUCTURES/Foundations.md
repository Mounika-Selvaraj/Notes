# 📘 Java Foundations for DSA: Programming Basics + Time & Space Complexity
---

## 📌 Table of Contents
### Programming Basics
1. [Java Program Structure](#1-java-program-structure)  
2. [Variables, Data Types, and Operators](#2-variables-data-types-and-operators)  
3. [Conditionals and Loops](#3-conditionals-and-loops)  
4. [Functions / Methods in Java](#4-functions--methods-in-java)  
5. [Arrays in Java](#5-arrays-in-java)  
6. [Strings in Java](#6-strings-in-java)

### Complexity Analysis
1. [Time Complexity (Big‑O)](#7-time-complexity)  
2. [Space Complexity](#8-space-complexity)  
3. [Best, Average, Worst Case](#9-best-average-worst-case)  
4. [Quick Reference Table](#10-quick-reference-table)

---

## 1. Java Program Structure

A minimal Java program has a **class** and a `main` method.

```java
public class DSAFoundations {
    public static void main(String[] args) {
        System.out.println("Hello, DSA!");
    }
}
```

- `public class DSAFoundations` → filename must be `DSAFoundations.java`.  
- `public static void main(String[] args)` → entry point of the program.  
- `System.out.println(...)` → prints to console.

---

## 2. Variables, Data Types, and Operators

### 2.1 Variables

A variable is a named storage location that holds a value.

```java
int age = 25;
double salary = 75000.50;
char grade = 'A';
boolean passed = true;
String name = "Alice";
```

### 2.2 Primitive Data Types

| Type      | Size (bytes) | Example                    |
|-----------|--------------|---------------------------|
| `byte`    | 1            | `byte b = 100;`           |
| `short`   | 2            | `short s = 30000;`        |
| `int`     | 4            | `int x = 1000000;`        |
| `long`    | 8            | `long l = 1000000000L;`   |
| `float`   | 4            | `float f = 1.5f;`         |
| `double`  | 8            | `double d = 3.14159;`     |
| `char`    | 2            | `char c = 'z';`           |
| `boolean` | 1 bit (approx)| `boolean flag = true;`  |

### 2.3 Operators

Common operators in DSA:

- Arithmetic: `+`, `-`, `*`, `/`, `%`
- Relational: `==`, `!=`, `<`, `<=`, `>`, `>=`
- Logical: `&&`, `||`, `!`
- Assignment: `=`, `+=`, `-=`, `*=`, `/=`, `%=`

Example:

```java
int a = 10, b = 3;
int sum = a + b;        // 13
int rem = a % b;        // 1
boolean check = a > b;  // true
```

---

## 3. Conditionals and Loops

### 3.1 Conditionals

```java
int age = 18;

if (age > 18) {
    System.out.println("Adult");
} else if (age == 18) {
    System.out.println("Just turned adult");
} else {
    System.out.println("Minor");
}
```

### 3.2 Loops

#### 3.2.1 `for` loop

```java
// print 0 to 9
for (int i = 0; i < 10; i++) {
    System.out.print(i + " ");
}
```

- `for(init; condition; update)`

#### 3.2.2 `while` loop

```java
int i = 0;
while (i < 10) {
    System.out.print(i + " ");
    i++;
}
```

#### 3.2.3 `do‑while` loop

```java
int i = 0;
do {
    System.out.print(i + " ");
    i++;
} while (i < 10);
```

**DSA usage tip:**  
Use `for` for arrays and fixed‑size iterations; use `while` for dynamic conditions.

---

## 4. Functions / Methods in Java

Functions (called **methods**) help modularize code.

### 4.1 Void method (no return)

```java
public static void greet(String name) {
    System.out.println("Hello, " + name + "!");
}

// usage
greet("Mounika");
```

### 4.2 Returning method

```java
public static int square(int x) {
    return x * x;
}

// usage
int result = square(5);  // 25
```

### 4.3 Multiple parameters

```java
public static int max(int a, int b) {
    if (a > b) {
        return a;
    } else {
        return b;
    }
}
```

In DSA, you often write helpers like:

```java
public static int findMax(int[] arr) { ... }
public static void reverseArray(int[] arr) { ... }
public static boolean isPalindrome(String s) { ... }
```

---

## 5. Arrays in Java

Arrays store multiple values of the **same type** in fixed size.

### 5.1 Declaration and Initialization

```java
// declare and create
int[] arr = new int;[1]

// declare and initialize with values
int[] nums = {10, 20, 30, 40, 50};

// access (index 0)
arr = 100;
System.out.println(nums);   // 10
```

### 5.2 Length and Iteration

```java
int length = nums.length;   // 5

// traditional for‑loop
for (int i = 0; i < nums.length; i++) {
    System.out.print(nums[i] + " ");
}

// enhanced for‑loop (for‑each)
for (int x : nums) {
    System.out.print(x + " ");
}
```

### 5.3 Arrays are mutable

```java
nums = 999;   // element changes in place[2]
```

---

## 6. Strings in Java

`String` is an **object**, not a primitive.

### 6.1 Declaration and Length

```java
String s1 = "Hello";
String s2 = new String("Hello");

int len = s1.length();              // 5
char c = s1.charAt(0);              // 'H'
```

### 6.2 Common Methods

```java
String s = "hello world";

System.out.println(s.toUpperCase());        // HELLO WORLD
System.out.println(s.substring(0, 5));      // hello
System.out.println(s.contains("world"));    // true
System.out.println(s.replace("world", "DSA")); // hello DSA
```

### 6.3 Immutability

```java
String s = "hi";
s = s + " there";   // new String created
```

### 6.4 String vs Array

| Feature        | Array                          | String                          |
|----------------|---------------------------------|----------------------------------|
| Type           | `int[]`, `char[]`              | `String` object                 |
| Mutability     | Mutable (elements change)      | Immutable (no in‑place change)  |
| Use case       | DSA containers (arr, stack)    | Text, substrings, sequences     |

Conversion:

```java
String s = "abc";
char[] chArr = s.toCharArray();
```

---

## 7. Time Complexity 

Time complexity describes **how fast / slow** code runs as input size `n` grows.

### 7.1 Key Big‑O Classes

| Notation      | Name            | Growth with `n`              |
|---------------|-----------------|------------------------------|
| `O(1)`        | Constant        | Independent of `n`           |
| `O(log n)`    | Logarithmic     | Very slow growth             |
| `O(n)`        | Linear          | Directly proportional to `n` |
| `O(n log n)`  | Linear‑log      | Common in sorting            |
| `O(n²)`       | Quadratic       | Grows fast with `n`          |
| `O(2ⁿ)`       | Exponential     | Very slow for large `n`      |

### 7.2 Code Examples

#### `O(1)` – Constant Time

```java
public static int getFirstElement(int[] arr) {
    return arr;   // O(1)
}
```

#### `O(log n)` – Binary Search

```java
public static int binarySearch(int[] arr, int target) {
    int left = 0, right = arr.length - 1;

    while (left <= right) {
        int mid = (left + right) / 2;

        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1;   // O(log n)
}
```

#### `O(n)` – Linear Loop

```java
public static int sumArray(int[] arr) {
    int sum = 0;
    for (int i = 0; i < arr.length; i++) {
        sum += arr[i];
    }
    return sum;   // O(n)
}
```

#### `O(n²)` – Nested Loops

```java
public static void printAllPairs(int[] arr) {
    for (int i = 0; i < arr.length; i++) {
        for (int j = 0; j < arr.length; j++) {
            System.out.println(arr[i] + " " + arr[j]);
        }
    }   // O(n²)
}
```

---

## 8. Space Complexity

Space complexity counts **extra memory** used as `n` grows.

### 8.1 Examples

#### `O(1)` – Constant Space

```java
public static int sum(int[] arr) {
    int sum = 0;
    for (int i = 0; i < arr.length; i++) {
        sum += arr[i];
    }
    return sum;   // only a few variables → O(1)
}
```

#### `O(n)` – Linear Space

```java
public static int[] copyArray(int[] arr) {
    int n = arr.length;
    int[] copy = new int[n];   // extra array of size n

    for (int i = 0; i < n; i++) {
        copy[i] = arr[i];
    }
    return copy;   // O(n) extra space
}
```

#### `O(n²)` – Quadratic Space

```java
public static int[][] createMatrix(int n) {
    int[][] matrix = new int[n][n];   // n×n space
    return matrix;   // O(n²)
}
```

---

## 9. Best, Average, Worst Case

### 9.1 Linear Search

```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            return i;
        }
    }
    return -1;
}
```

- **Best case**: `target` at index `0` → `O(1)`  
- **Average case**: `target` in the middle → `O(n)`  
- **Worst case**: `target` not present or at end → `O(n)`

### 9.2 Binary Search

```java
public static int binarySearch(int[] arr, int target) {
    int left = 0, right = arr.length - 1;

    while (left <= right) {
        int mid = (left + right) / 2;

        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1;   // O(log n) in worst / average case
}
```

- **Best case**: hit at first mid → `O(1)`  
- **Worst / Average**: `log n` steps → `O(log n)`

---

## 10. Quick Reference Table 

| Concept                   | Java Code Snippet                             | Time Complexity | Space Complexity |
|---------------------------|-----------------------------------------------|-----------------|------------------|
| Access array element      | `arr[i]`                                      | O(1)            | O(1)             |
| Single loop over array    | `for (int i = 0; i < n; i++)`                | O(n)            | O(1)             |
| Nested loop over array    | two `for` loops over `n`                     | O(n²)           | O(1)             |
| Binary search loop        | while with `mid` on sorted array             | O(log n)        | O(1)             |
| Copy array                | `new int[n]` and fill in loop                | O(n)            | O(n)             |
| Allocate 2D matrix        | `new int[n][n]`                              | O(1) to allocate| O(n²)            |

---
