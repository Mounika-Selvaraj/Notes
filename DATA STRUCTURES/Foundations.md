# Java DSA – Programming Basics & Complexity (Beginner)

## Table of Contents
- [1. Java Programming Basics](#1-java-programming-basics)
  - [1.1 Variables and Types](#11-variables-and-types)
  - [1.2 Operators and Expressions](#12-operators-and-expressions)
  - [1.3 Control Flow: Loops and Conditionals](#13-control-flow-loops-and-conditionals)
  - [1.4 Functions in Java (Methods)](#14-functions-in-java-methods)
  - [1.5 Arrays](#15-arrays)
  - [1.6 Strings](#16-strings)
  - [1.7 Recursion Basics](#17-recursion-basics)
- [2. Complexity Analysis and Big-O](#2-complexity-analysis-and-big-o)
  - [2.1 Why Complexity?](#21-why-complexity)
  - [2.2 Common Big-O Classes](#22-common-big-o-classes)
  - [2.3 Time Complexity in Simple Java Code](#23-time-complexity-in-simple-java-code)
  - [2.4 Space Complexity Basics](#24-space-complexity-basics)
  - [2.5 Quick Complexity Reference Table](#25-quick-complexity-reference-table)

---

## 1. Java Programming Basics

### 1.1 Variables and Types

In Java, every variable has:

- A **type** (what kind of data it holds)  
- A **name**  
- An optional **initial value**

General form:

```java
type name = value;
```

**Common primitive types:**

- `int`   → integers (e.g., 10, -3)  
- `long`  → larger integers  
- `double` → decimal numbers  
- `float` → smaller decimal numbers  
- `char`  → single character (e.g., 'a')  
- `boolean` → `true` or `false`  
- `byte`, `short` → smaller integer ranges  

**Reference types:**

- `String`, arrays (`int[]`), classes (`Scanner`, `ArrayList`, your own classes)

Example:

```java
int age = 21;
double price = 99.99;
char grade = 'A';
boolean isPassed = true;
String name = "Mounika";
```

**Naming rules (recommended):**

- Start with a letter or `_`
- No spaces or special symbols (except `_` and digits after first character)
- Use `camelCase` for variables, e.g., `totalMarks`

---

### 1.2 Operators and Expressions

Operators combine variables and values to form **expressions**.

**Arithmetic operators:**

- `+`, `-`, `*`, `/`, `%`

**Comparison operators:**

- `==`, `!=`, `>`, `<`, `>=`, `<=`

**Logical operators:**

- `&&` (AND)  
- `||` (OR)  
- `!` (NOT)

Example:

```java
int a = 5, b = 3;

int sum = a + b;                    // 8
boolean bigger = a > b;             // true
boolean condition = (a > 2) && (b < 10); // true
```

---

### 1.3 Control Flow: Loops and Conditionals

#### If / else

```java
int marks = 82;

if (marks >= 90) {
    System.out.println("A");
} else if (marks >= 75) {
    System.out.println("B");
} else {
    System.out.println("C or below");
}
```

#### `for` loop

Use when you know how many times to repeat.

```java
for (int i = 0; i < 5; i++) {
    System.out.println("i = " + i);
}
```

#### `while` loop

Use when you loop until a condition becomes false.

```java
int i = 0;
while (i < 5) {
    System.out.println("i = " + i);
    i++;
}
```

#### `do-while` loop

Executes the body at least once.

```java
int x = 0;
do {
    System.out.println(x);
    x++;
} while (x < 5);
```

---

### 1.4 Functions in Java (Methods)

In Java, functions are called **methods** and they belong to a class.

General form:

```java
returnType methodName(parameterType1 p1, parameterType2 p2) {
    // body
    return someValue; // if returnType is not void
}
```

Example: method that adds two integers

```java
public class Main {

    public static int add(int a, int b) {
        int sum = a + b;
        return sum;
    }

    public static void main(String[] args) {
        int result = add(3, 4);
        System.out.println(result);  // 7
    }
}
```

Notes:

- `void` → no return value  
- Method parameters are **local** to that method  
- `static` lets you call the method without creating an object of the class (handy for DSA practice)

---

### 1.5 Arrays

An array is a **fixed-size** sequence of elements of the **same type**.

Declaration and initialization:

```java
int[] arr = new int;              // all elements default to 0[1]
int[] nums = {1, 2, 3, 4, 5};        // initialized with values
String[] names = {"A", "B", "C"};
```

Accessing elements (0-based index):

```java
int first = nums;                 // 1
nums = 10;                        // change 3 → 10[2]
int length = nums.length;            // 5
```

Looping through an array:

```java
for (int i = 0; i < nums.length; i++) {
    System.out.println(nums[i]);
}

// enhanced for loop
for (int x : nums) {
    System.out.println(x);
}
```

Key points:

- Size is fixed when created  
- Access by index (`arr[i]`) is constant-time (O(1))

---

### 1.6 Strings

In Java:

- `String` is a **class** (reference type)  
- Strings are **immutable** → once created, the content cannot change; operations create new strings

Creating strings:

```java
String s1 = "hello";
String s2 = new String("world");
```

Common operations:

```java
int len = s1.length();               // length
char c = s1.charAt(0);               // 'h'
String s3 = s1 + " " + s2;           // "hello world"
boolean eq = s1.equals("hello");     // true
String upper = s1.toUpperCase();     // "HELLO"
String sub = s1.substring(1, 4);     // "ell"
```

Looping through characters:

```java
for (int i = 0; i < s1.length(); i++) {
    char ch = s1.charAt(i);
    System.out.println(ch);
}
```

For heavy string modifications (e.g., in loops), use `StringBuilder`:

```java
StringBuilder sb = new StringBuilder();

for (int i = 0; i < 5; i++) {
    sb.append(i).append(" ");
}

String result = sb.toString();
System.out.println(result);
```

---

### 1.7 Recursion Basics

**Recursion**: a method that calls itself to solve a problem by reducing it to smaller subproblems.

Two critical parts:

- **Base case** → when to stop recursing  
- **Recursive case** → call the same method with a smaller/simpler input

#### Example: factorial

Mathematically:

- `0! = 1`  
- `n! = n * (n - 1)!` for `n > 0`

Java code:

```java
public class Main {

    public static int factorial(int n) {
        if (n == 0) {          // base case
            return 1;
        }
        return n * factorial(n - 1);  // recursive call
    }

    public static void main(String[] args) {
        System.out.println(factorial(5)); // 120
    }
}
```

#### Example: sum of array elements using recursion

```java
public class Main {

    public static int sumArray(int[] arr, int index) {
        if (index == arr.length) {   // base case: no elements left
            return 0;
        }
        // current element + sum of the rest
        return arr[index] + sumArray(arr, index + 1);
    }

    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 4};
        int sum = sumArray(nums, 0);
        System.out.println(sum);   // 10
    }
}
```

This `sumArray` method:

- Time complexity: O(n) (one call per element)  
- Space complexity: O(n) (recursion stack frames)

---

## 2. Complexity Analysis and Big-O

### 2.1 Why Complexity?

**Complexity analysis** studies how:

- **Running time** grows with input size `n` → *time complexity*  
- **Memory usage** grows with input size `n` → *space complexity*

**Big-O notation** describes an *upper bound* on growth, ignoring constants and lower-order terms.  
It answers: “How does it scale when `n` becomes very large?”

---

### 2.2 Common Big-O Classes

#### O(1) – Constant time

Running time does **not** depend on input size.

Examples:

```java
int x = arr;       // direct index access[1]
int y = a + b;        // simple arithmetic
```

#### O(log n) – Logarithmic time

Each step cuts the problem size by a constant factor (e.g., half).

Example: **binary search** on a sorted array.

```java
public static int binarySearch(int[] arr, int target) {
    int low = 0;
    int high = arr.length - 1;

    while (low <= high) {
        int mid = (low + high) / 2;

        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }

    return -1; // not found
}
```

#### O(n) – Linear time

Work grows **directly** with `n`.

Example: traverse an array once.

```java
public static int sum(int[] arr) {
    int s = 0;
    for (int i = 0; i < arr.length; i++) {
        s += arr[i];    // constant work inside loop
    }
    return s;           // total O(n)
}
```

#### O(n log n) – n log n time

Appears in many **divide and conquer** algorithms and efficient sorting algorithms like `MergeSort` and average-case `QuickSort`.

Very common in real-world DSA.

#### O(n²) – Quadratic time

Often from **nested loops** over the same input:

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        // constant work
    }
}
```

Examples: naive Bubble Sort, Selection Sort, Insertion Sort (worst case).

#### Higher orders (usually bad for large n)

- **O(2ⁿ)** – exponential time (many naive recursive solutions)  
- **O(n!)** – factorial time (e.g., generating all permutations)

---

### 2.3 Time Complexity in Simple Java Code

#### Example 1 – Array access

```java
int x = arr;  // O(1)[1]
```

#### Example 2 – Single loop

```java
for (int i = 0; i < n; i++) {
    // O(1) work
}
// Total: O(n)
```

#### Example 3 – Nested loop

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        // O(1) work
    }
}
// Total: O(n^2)
```

#### Example 4 – Binary search (on sorted array)

```java
int low = 0;
int high = arr.length - 1;

while (low <= high) {
    int mid = (low + high) / 2;

    if (arr[mid] == target) {
        // found
        break;
    } else if (arr[mid] < target) {
        low = mid + 1;
    } else {
        high = mid - 1;
    }
}
// Time: O(log n)
```

---

### 2.4 Space Complexity Basics

Space complexity measures **extra memory** used by the algorithm (besides input).

Things that contribute:

- Variables  
- Extra arrays, collections  
- Recursion stack frames  

Examples:

- A loop using only a few variables:

  ```java
  int s = 0;
  for (int i = 0; i < n; i++) {
      s += arr[i];
  }
  ```

  Space complexity: **O(1)** (constant extra space)

- Algorithm that creates a new array of size `n`:

  ```java
  int[] copy = new int[n];
  ```

  Space complexity: **O(n)**

- Recursive function with maximum depth `n` and constant work per call → **O(n)** extra stack space.

For `sumArray` from earlier:

- Time: O(n)  
- Space: O(n) (due to recursion depth)

---

### 2.5 Quick Complexity Reference Table

| Concept              | Java Example / Idea                      | Typical Complexity      |
|----------------------|------------------------------------------|-------------------------|
| Array access         | `arr[i]`                                 | O(1) time, O(1) space   |
| Full array traversal | `for (int x : arr)`                      | O(n) time, O(1) space   |
| Nested loops on n    | double `for` over same array            | O(n²) time, O(1) space  |
| Binary search        | loop halving search space               | O(log n) time           |
| Simple recursion     | factorial, recursive array sum          | O(n) time, O(n) space   |

---

> ✏️ **Practice prompt:**  
> Create a Java method that takes an `int[]` and returns `true` if the array contains a target value using:
> 1) a simple linear scan (loop), and  
> 2) binary search (assuming the array is sorted).  
> For each version, what is the time complexity and why?
