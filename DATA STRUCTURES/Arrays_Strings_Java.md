# 🟡 Arrays & Strings Deep Dive – DSA Notes (Java)

## 📌 Table of Contents

### Arrays
1. [What is an Array?](#1-what-is-an-array)  
2. [Declaration, Initialization, and Access](#2-declaration-initialization-and-access)  
3. [Array Traversal](#3-array-traversal)  
4. [Insertion & Deletion in Arrays](#4-insertion--deletion-in-arrays)  
5. [Common Array Operations (Min, Max, Search, Reverse)](#5-common-array-operations)  
6. [Multidimensional Arrays (2D Arrays)](#6-multidimensional-arrays-2d-arrays)  

### Strings
1. [What is a String?](#7-what-is-a-string)  
2. [String Creation and Length](#8-string-creation-and-length)  
3. [String Methods (Essential for DSA)](#9-string-methods-essential-for-dsa)  
4. [String Traversal & Char‑by‑char Processing](#10-string-traversal-Char_by_char-Processing)  
5. [String Problems (Palindromes, Two Pointers, Substrings)](#11-string-problems)  

---

### Recursion & Backtracking

1. [What is Recursion?](#1-what-is-recursion)  
2. [Key Components of a Recursive Function](#2-key-components-of-a-recursive-function)  
3. [Basic Recursion Examples (Java)](#3-basic-recursion-examples-java)  
4. [Recursion vs Iteration](#4-recursion-vs-iteration)  
5. [Common Patterns in Recursion](#5-common-patterns-in-recursion)  
6. [Introduction to Backtracking](#6-introduction-to-backtracking)  
7. [Classic Backtracking Problems in Java](#7-classic-backtracking-problems-in-java)  
8. [Recursion & Backtracking Best Practices](#8-recursion--backtracking-best-practices)  

---
## 1. What is an Array?

- An **array** is a **fixed‑size** container that stores multiple elements of the **same type**.  
- Elements are stored in **contiguous memory** and accessed by **index** (0‑based).  
- Arrays are **mutable**: you can change individual elements but **not the size**.

---

## 2. Declaration, Initialization, and Access

### 2.1 Declaration

```java
int[] arr;           // declare reference
int[] nums = new int;  // declare and create array of size 5[1]
```

### 2.2 Initialization with values

```java
int[] nums = {10, 20, 30, 40, 50};

// 2D array (matrix)
int[][] matrix = {
    {1, 2},
    {3, 4},
    {5, 6}
};
```

### 2.3 Access and update

```java
int[] nums = {10, 20, 30, 40, 50};

nums = 100;          // modify element at index 0
int val = nums;      // read element at index 2 → 30[2]
int n = nums.length;    // 5
```

---

## 3. Array Traversal

### 3.1 Using classic `for` loop

```java
public static void printArray(int[] arr) {
    for (int i = 0; i < arr.length; i++) {
        System.out.print(arr[i] + " ");
    }
    System.out.println();
}
```

**Time:** `O(n)`, **Space:** `O(1)`.

### 3.2 Using enhanced for loop (for‑each)

```java
public static void printArrayEnhanced(int[] arr) {
    for (int x : arr) {
        System.out.print(x + " ");
    }
    System.out.println();
}
```

Best when you **don’t need the index**.

### 3.3 Reverse traversal

```java
public static void printReverse(int[] arr) {
    for (int i = arr.length - 1; i >= 0; i--) {
        System.out.print(arr[i] + " ");
    }
    System.out.println();
}
```

---

## 4. Insertion & Deletion in Arrays

Arrays are **fixed‑size**, so insertion and deletion require **shifting**.

### 4.1 Insertion at a given index

```java
// Returns whether insertion is possible
public static boolean insertAt(int[] arr, int n, int pos, int value) {
    // n = current filled size; assume arr.length > n
    if (pos < 0 || pos > n || n >= arr.length) {
        return false;
    }

    // shift right from pos onwards
    for (int i = n - 1; i >= pos; i--) {
        arr[i + 1] = arr[i];
    }

    arr[pos] = value;
    return true;   // Time: O(n), Space: O(1)
}
```

**Example usage:**

```java
int[] arr = new int;[3]
arr = 10; arr = 20; arr = 30;[4][2]
int n = 3;

insertAt(arr, n, 1, 999);   //[5][6][3]
n++;   // current size becomes 4
```

### 4.2 Deletion at a given index

```java
public static boolean deleteAt(int[] arr, int n, int pos) {
    if (pos < 0 || pos >= n) {
        return false;
    }

    // shift left from pos+1 to end
    for (int i = pos + 1; i < n; i++) {
        arr[i - 1] = arr[i];
    }

    n--;   // decrease size
    return true;   // Time: O(n), Space: O(1)
}
```

**Example:**

```java
int[] arr = {10, 20, 30, 40};
int n = 4;

deleteAt(arr, n, 1);   // removes 20 at index 1
n--;   // n becomes 3
// logical array:[7][6][3]
```

---

## 5. Common Array Operations

### 5.1 Find Min & Max

```java
public static int findMax(int[] arr) {
    if (arr.length == 0) {
        throw new IllegalArgumentException("Array cannot be empty");
    }

    int max = arr;
    for (int i = 1; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    return max;   // O(n)
}

public static int findMin(int[] arr) {
    if (arr.length == 0) {
        throw new IllegalArgumentException("Array cannot be empty");
    }

    int min = arr;
    for (int i = 1; i < arr.length; i++) {
        if (arr[i] < min) {
            min = arr[i];
        }
    }
    return min;   // O(n)
}
```

### 5.2 Linear Search

```java
public static int linearSearch(int[] arr, int target) {
    for (int i = 0; i < arr.length; i++) {
        if (arr[i] == target) {
            return i;   // index found
        }
    }
    return -1;   // not found
}
```

Best case: `O(1)`, Worst/Average: `O(n)`.

### 5.3 Reverse an Array (in‑place)

```java
public static void reverseArray(int[] arr) {
    int left = 0;
    int right = arr.length - 1;

    while (left < right) {
        int temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;
        left++;
        right--;
    }
}
```

**Time:** `O(n/2) ≈ O(n)`, **Space:** `O(1)`.

---

## 6. Multidimensional Arrays (2D Arrays)

### 6.1 Declaration and initialization

```java
int[][] matrix = new int;   // 3 rows, 4 cols[8][9]

int[][] fixed = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

### 6.2 Traversal (row‑wise, column‑wise)

```java
public static void printMatrixRowWise(int[][] matrix) {
    int rows = matrix.length;
    int cols = matrix.length;

    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            System.out.print(matrix[i][j] + " ");
        }
        System.out.println();
    }
}
```

### 6.3 Sum of all elements

```java
public static int matrixSum(int[][] matrix) {
    int sum = 0;
    for (int[] row : matrix) {
        for (int val : row) {
            sum += val;
        }
    }
    return sum;   // O(rows × cols)
}
```

---

## 7. What is a String?

- A `String` is an **object** of the `java.lang.String` class.  
- It represents an **immutable** sequence of characters.  
- Strings are stored in the **heap**, with automatic optimizations like the **string pool**.

---

## 8. String Creation and Length

### 8.1 String creation

```java
String s1 = "Hello";                  // from string pool
String s2 = new String("Hello");      // forces new object

String s3 = "Hel" + "lo";             // string concatenation
```

### 8.2 Length and char access

```java
String s = "Java";

int len = s.length();              // 4
char first = s.charAt(0);          // 'J'
char last = s.charAt(len - 1);     // 'a'
```

---

## 9. String Methods (Essential for DSA)

### 9.1 Basic utility methods

```java
String s = " hello world ";

System.out.println(s.length());            // 13
System.out.println(s.trim());              // "hello world"
System.out.println(s.toUpperCase());       // " HELLO WORLD "
System.out.println(s.toLowerCase());       // " hello world "
System.out.println(s.contains("world"));   // true
System.out.println(s.startsWith(" hel"));  // true
System.out.println(s.endsWith("d "));      // true
```

### 9.2 Substring & replace

```java
String s = "hello world";

System.out.println(s.substring(0, 5));     // "hello"
System.out.println(s.substring(6));        // "world"

System.out.println(s.replace('o', '*'));
// replaces all chars: "hell* w*rld"

System.out.println(s.replace("ll", "LL"));
// "heLLo world"
```

### 9.3 Comparison and splitting

```java
String s1 = "hello";
String s2 = "hello";
String s3 = new String("hello");

System.out.println(s1 == s2);        // true (same in pool)
System.out.println(s1 == s3);        // false (different object)
System.out.println(s1.equals(s3));   // true (same content)

String csv = "a,b,c,d";
String[] parts = csv.split(",");     // ["a", "b", "c", "d"]
```

---

## 10. String Traversal & Char_by_char Processing

### 10.1 Index‑based traversal

```java
public static void printChars(String s) {
    for (int i = 0; i < s.length(); i++) {
        System.out.print(s.charAt(i) + " ");
    }
    System.out.println();
}
```

**Time:** `O(n)`.

### 10.2 Enhanced for‑loop (via `toCharArray`)

```java
public static void printCharsEnhanced(String s) {
    for (char c : s.toCharArray()) {
        System.out.print(c + " ");
    }
    System.out.println();
}
```

Takes `O(n)` time and `O(n)` extra space due to copying to char array.

---

## 11. String Problems (Examples for DSA Practice)

### 11.1 Palindrome Check (Two Pointers)

```java
public static boolean isPalindrome(String s) {
    int left = 0;
    int right = s.length() - 1;

    while (left < right) {
        if (s.charAt(left) != s.charAt(right)) {
            return false;
        }
        left++;
        right--;
    }
    return true;
}
```

**Time:** `O(n/2) ≈ O(n)`, **Space:** `O(1)`.

### 11.2 Count vowels in a string

```java
public static int countVowels(String s) {
    String vowels = "aeiouAEIOU";
    int count = 0;

    for (char c : s.toCharArray()) {
        if (vowels.indexOf(c) != -1) {
            count++;
        }
    }
    return count;   // O(n)
}
```

### 11.3 Reverse a string (in‑place using `StringBuilder`)

```java
public static String reverseString(String s) {
    StringBuilder sb = new StringBuilder(s);
    sb.reverse();   // O(n)
    return sb.toString();
}
```

`StringBuilder` is **mutable**, so it’s much more efficient than repeatedly concatenating `String` objects.

### 11.4 Longest Substring Without Repeating Characters (DSA‑style)

```java
import java.util.HashSet;

public static int longestSubstringWithoutRepeating(String s) {
    int n = s.length();
    int left = 0;
    int maxLen = 0;
    HashSet<Character> seen = new HashSet<>();

    for (int right = 0; right < n; right++) {
        char c = s.charAt(right);

        while (seen.contains(c)) {
            seen.remove(s.charAt(left));
            left++;
        }

        seen.add(c);
        maxLen = Math.max(maxLen, right - left + 1);
    }

    return maxLen;   // O(n), Space: O(1) (bounded by alphabet size)
}
```

**Example:**

```java
String s = "abcabcbb";
int ans = longestSubstringWithoutRepeating(s);   // 3 ("abc")
```

---

## Quick Reference Table: Arrays vs Strings

| Aspect              | Arrays (Java)                                       | Strings (Java)                                     |
|---------------------|-----------------------------------------------------|----------------------------------------------------|
| Type                | `int[]`, `char[]`, etc.                            | `String` object                                    |
| Mutability          | Mutable elements                                   | Immutable (no in‑place change)                    |
| Size                | Fixed at creation (`arr.length`)                   | `s.length()`                                      |
| Modification        | `arr[i] = x`                                       | `s = s + "new"` → new object                      |
| Best for            | Numbers, indices, DSA structures                    | Text, substrings, patterns                         |
| Typical DSA tools   | Two pointers, sliding window, prefix sum           | Two pointers, sliding window, char‑array, `equals()` |







## 1. What is Recursion?

**Recursion** is a technique where a **function calls itself** to solve a problem by **breaking it into smaller, similar sub‑problems**.

- The **same logic** is applied repeatedly on smaller inputs.  
- Used massively in **trees, graphs, divide‑and‑conquer, memoization, and backtracking**.

---

## 2. Key Components of a Recursive Function

Every clean recursive function must have:

1. **Base Case(s)**  
   - Stopping condition that terminates recursion.  
   - Prevents infinite calls and `StackOverflowError`.

2. **Recursive Case**  
   - Calls the same function with a **smaller or simpler input**.  
   - Must move toward the base case.

3. **Work before/after the call**  
   - You can do computation **before** the call, **after** the call, or **around** it.

---

## 3. Basic Recursion Examples (Java)

### 3.1 Factorial

```java
public static int factorial(int n) {
    // Base case
    if (n <= 1) {
        return 1;
    }

    // Recursive case
    return n * factorial(n - 1);
}

// Usage
int ans = factorial(5);   // 120
```

- **Time:** `O(n)`, **Space:** `O(n)` (stack depth).

### 3.2 Fibonacci

```java
public static int fibonacci(int n) {
    // Base cases
    if (n == 0) {
        return 0;
    }
    if (n == 1) {
        return 1;
    }

    // Recursive case
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// Print first 10
for (int i = 0; i < 10; i++) {
    System.out.print(fibonacci(i) + " ");
}
// Output: 0 1 1 2 3 5 8 13 21 34
```

Without memoization, this is `O(2ⁿ)` time due to overlapping subproblems.

### 3.3 Sum of Array (Recursive)

```java
public static int sumArray(int[] arr, int n) {
    // Base case: no elements left
    if (n == 0) {
        return 0;
    }

    // Include last element and recurse on n-1
    return arr[n - 1] + sumArray(arr, n - 1);
}

// Usage
int[] arr = {1, 2, 3, 4, 5};
int total = sumArray(arr, arr.length);   // 15
```

Time: `O(n)`, Space: `O(n)` (stack).

### 3.4 Power of a Number

```java
public static int power(int base, int exp) {
    // Base case
    if (exp == 0) {
        return 1;
    }

    // Recursive case
    return base * power(base, exp - 1);
}

// Usage
int ans = power(2, 5);   // 32
```

For better performance, you can use **divide‑and‑conquer** (power in `O(log n)`).

---

## 4. Recursion vs Iteration

| Feature              | Recursion                                  | Iteration                                  |
|----------------------|--------------------------------------------|---------------------------------------------|
| Code style           | Often **cleaner and shorter**              | More **explicit** (loops)                   |
| Call stack           | Uses **stack memory** (`O(n)` depth)      | Uses **constant stack space** (mostly)     |
| Readability          | Very good for tree‑like problems           | Good for simple linear flows               |
| Risk                 | Stack overflow if poorly bounded          | No stack overflow (but infinite loops)     |
| Typical for          | Trees, graphs, backtracking, DP            | Simple loops, basic DSA patterns           |

**Example: Factorial – Iterative**

```java
public static int factorialIterative(int n) {
    int f = 1;
    for (int i = 2; i <= n; i++) {
        f *= i;
    }
    return f;
}
```

---

## 5. Common Patterns in Recursion

### 5.1 Linear Recursion

The function makes **one recursive call** per stack frame.

```java
public static void printNumbers(int n) {
    if (n == 0) {
        return;
    }
    System.out.print(n + " ");
    printNumbers(n - 1);
}
```

Prints: `5 4 3 2 1`

### 5.2 Tail Recursion

The recursive call is the **last operation**, and **nothing happens after it**.

```java
public static int factorialTail(int n, int accumulator) {
    if (n <= 1) {
        return accumulator;
    }
    return factorialTail(n - 1, accumulator * n);
}

// Usage
int ans = factorialTail(5, 1);
```

In theory, some compilers optimize this into a loop (but Java doesn’t do tail‑call optimization in practice).

### 5.3 Tree / Branching Recursion

Function makes **multiple recursive calls**, creating a tree‑like call stack.

```java
public static void printBinaryTree(int n) {
    if (n <= 0) {
        return;
    }
    System.out.print(n + " ");
    printBinaryTree(n - 1);   // left
    printBinaryTree(n - 1);   // right (same logic, different branch)
}
```

Each call branches twice, leading to a **binary recursion tree**.

---

## 6. Introduction to Backtracking

**Backtracking** is a **recursive algorithmic technique** where you:

1. Explore all possible choices step by step.  
2. Build a **partial solution**.  
3. If it **violates constraints**, **undo** that choice and try a different path.  
4. When you have a **valid complete solution**, record or return it.

It follows this pattern:

> **Choose → Explore → Un‑choose (backtrack)**

### 6.1 General Backtracking Template

```java
public static void backtrack(List<Integer> path, int[] options) {
    // If path is valid complete solution, print/collect
    if (isComplete(path)) {
        System.out.println(path);
        return;
    }

    for (int option : options) {
        // 1. Choose
        path.add(option);

        // 2. Explore (recursively)
        backtrack(path, options);

        // 3. Un‑choose (backtrack)
        path.remove(path.size() - 1);
    }
}
```

Why it works:
- You **temporarily make a choice**, explore further.  
- If it doesn’t lead to a good solution, you **remove that choice** and try the next.

---

## 7. Classic Backtracking Problems in Java

### 7.1 Permutations of Array (Backtracking)

Given an array of distinct integers, generate **all permutations**.

```java
import java.util.*;

public class Permutations {

    public static void permutationBacktrack(List<Integer> path, boolean[] used, int[] nums, List<List<Integer>> res) {
        // Base: if path size == nums.length, we have a valid permutation
        if (path.size() == nums.length) {
            res.add(new ArrayList<>(path));
            return;
        }

        for (int i = 0; i < nums.length; i++) {
            if (!used[i]) {
                // 1. Choose
                path.add(nums[i]);
                used[i] = true;

                // 2. Explore
                permutationBacktrack(path, used, nums, res);

                // 3. Un‑choose
                path.remove(path.size() - 1);
                used[i] = false;
            }
        }
    }

    public static List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        List<Integer> path = new ArrayList<>();
        boolean[] used = new boolean[nums.length];

        permutationBacktrack(path, used, nums, result);
        return result;
    }

    // Usage
    public static void main(String[] args) {
        int[] nums = {1, 2, 3};
        List<List<Integer>> perms = permute(nums);
        for (List<Integer> p : perms) {
            System.out.println(p);
        }
    }
}
```

- **Time:** `O(n! × n)` (n! permutations, each list copy is `O(n)`).  
- **Space:** `O(n)` depth of recursion + storage for output.

### 7.2 Subsets (Power Set)

Given an array, generate **all subsets**.

```java
import java.util.*;

public class Subsets {

    public static void subsetBacktrack(int[] nums, int index, List<Integer> path, List<List<Integer>> res) {
        // Every path is a valid subset (no constraint)
        res.add(new ArrayList<>(path));

        // Consider elements from index onwards
        for (int i = index; i < nums.length; i++) {
            // 1. Choose nums[i]
            path.add(nums[i]);

            // 2. Explore
            subsetBacktrack(nums, i + 1, path, res);

            // 3. Backtrack
            path.remove(path.size() - 1);
        }
    }

    public static List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        List<Integer> path = new ArrayList<>();

        subsetBacktrack(nums, 0, path, result);
        return result;
    }

    // Usage
    public static void main(String[] args) {
        int[] nums = {1, 2, 3};
        List<List<Integer>> subs = subsets(nums);
        for (List<Integer> s : subs) {
            System.out.println(s);
        }
    }
}
```

- **Time:** `O(2ⁿ)`, because there are `2ⁿ` subsets.  
- **Space:** `O(n)` depth + `O(2ⁿ)` for storing all subsets.

### 7.3 Combination Sum (Unbounded Choices)

Given a set of candidate numbers and a target, find **all unique combinations** where the candidate numbers sum to target.

```java
import java.util.*;

public class CombinationSum {

    public static void combinationSumBacktrack(int[] candidates, int target, int start, List<Integer> path, List<List<Integer>> res) {
        if (target == 0) {
            res.add(new ArrayList<>(path));
            return;
        }
        if (target < 0) {
            return;   // no solution from this path
        }

        for (int i = start; i < candidates.length; i++) {
            // 1. Choose
            path.add(candidates[i]);

            // 2. Explore (allow reuse of same element, so i not i+1)
            combinationSumBacktrack(candidates, target - candidates[i], i, path, res);

            // 3. Backtrack
            path.remove(path.size() - 1);
        }
    }

    public static List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();
        List<Integer> path = new ArrayList<>();

        combinationSumBacktrack(candidates, target, 0, path, result);
        return result;
    }
}
```

This can be **adjusted for “no reuse”**:

- Use `i + 1` instead of `i` in the recursive call.

---

## 8. Recursion & Backtracking Best Practices

- ✅ **Always handle base cases clearly** to avoid infinite recursion.  
- ✅ **Ensure the parameter is moving toward the base case** (e.g., `n → n-1`, `index → i+1`).  
- ✅ **Use `ArrayList` and `boolean[]`/`Set`** to track choices and visited states in backtracking.  
- ✅ **Remove the last element after recursion** (`list.remove(size-1)`) to **backtrack**.  
- ✅ **Avoid deep recursion on large inputs**; consider iterative alternatives or memoization if possible.  
- ✅ **For tree‑based problems** (paths, DFS), recursion is natural and elegant; leverage it heavily.  

---

You can now save this file as `Recursion_Backtracking_Java_DSA.md` and use it as your **single, detailed GitHub‑ready notebook** for Recursion and Backtracking in Java.
