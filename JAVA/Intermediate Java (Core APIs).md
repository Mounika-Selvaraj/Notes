# Intermediate Java (Core APIs)

## Table of Contents
### Intermediate Java: Core APIs - Strings
- [Introduction to Strings](#introduction-to-strings)
- [String Immutability](#string-immutability)
- [String vs StringBuilder vs StringBuffer](#string-vs-stringbuilder-vs-stringbuffer)
- [String Class](#string-class)
- [StringBuilder Class](#stringbuilder-class)
- [StringBuffer Class](#stringbuffer-class)
- [Common String Methods](#common-string-methods)
- [Performance Comparison](#performance-comparison)
- [Best Practices](#best-practices)
- [Code Examples](#code-examples)

### Intermediate Java: Core APIs - Arrays
- [Introduction to Arrays](#introduction-to-arrays)
- [Single-Dimensional Arrays](#single-dimensional-arrays)
- [Multi-Dimensional Arrays](#multi-dimensional-arrays)
- [Jagged Arrays](#jagged-arrays)
- [Array Declaration and Initialization](#array-declaration-and-initialization)
- [Accessing Array Elements](#accessing-array-elements)
- [Arrays Utility Class](#arrays-utility-class)
- [Common Arrays Methods](#common-arrays-methods)
- [Performance Considerations](#performance-considerations)
- [Best Practices](#best-practices)
- [Code Examples](#code-examples)

## Introduction to Strings
Strings are fundamental in Java for handling text data. They represent sequences of characters and are used everywhere from user input to configuration files. Java provides three main classes for string manipulation: **String**, **StringBuilder**, and **StringBuffer**.

![Java Strings overview](https://pplx-res.cloudinary.com/image/upload/v1/java-core/strings-overview-diagram.png)

## String Immutability
Java Strings are **immutable**, meaning once created, their value cannot be changed. Any modification operation like `concat()` or `replace()` creates a **new String object**, leaving the original unchanged. This design ensures thread-safety and allows String objects to be cached in the **String pool**.

![String immutability diagram](https://pplx-res.cloudinary.com/image/upload/v1/java-core/string-immutability.png)

Immutability provides security benefits as Strings are used in class loading and cannot be altered maliciously.

## String vs StringBuilder vs StringBuffer

| Feature | String | StringBuilder | StringBuffer |
|---------|--------|---------------|--------------|
| **Mutability** | Immutable | Mutable | Mutable |
| **Thread-Safety** | Yes (due to immutability) | No | Yes (synchronized methods) |
| **Performance** | Slow for repeated modifications | **Fastest** | Slower than StringBuilder |
| **Introduced In** | Java 1.0 | Java 1.5 | Java 1.0 |
| **Memory Usage** | Creates new objects | Modifies in-place | Modifies in-place |
| **Use Case** | Fixed text | Single-threaded concatenation | Multi-threaded concatenation |

**StringBuilder** (since Java 5) replaced StringBuffer in most cases due to better performance in single-threaded environments.

![String vs StringBuilder vs StringBuffer comparison](https://pplx-res.cloudinary.com/image/upload/v1/java-core/strings-comparison-chart.png)

## String Class
The **String class** is **final** and represents constant sequences of characters. It uses a `char[]` array internally but is immutable. Strings are stored in a **pool** for reuse.

**Key characteristics:**
- Created via literals: `String s = "Hello";`
- Methods return **new Strings**
- **HashCode** is cached for performance

## StringBuilder Class
**StringBuilder** is **mutable** and **not thread-safe**, making it faster than StringBuffer. It's ideal for string manipulations in single-threaded code. Introduced in Java 5 as a modern alternative.

**Main methods:** `append()`, `insert()`, `delete()`, `reverse()`.

## StringBuffer Class
**StringBuffer** is similar to StringBuilder but **thread-safe** due to synchronized methods. Use it only when thread safety is required. It's legacy but still used in multi-threaded scenarios.

All mutating methods are **synchronized**, adding overhead.

## Common String Methods

| Method | Description | Return Type | Example |
|--------|-------------|-------------|---------|
| `length()` | Returns string length | `int` | `"hello".length()` → 5 |
| `charAt(int)` | Char at index | `char` | `"hello".charAt(0)` → 'h' |
| `substring(int)` | Substring from index | `String` | `"hello".substring(1)` → "ello" |
| `indexOf(String)` | First occurrence index | `int` | `"hello".indexOf("l")` → 2 |
| `lastIndexOf(String)` | Last occurrence index | `int` | `"hello".lastIndexOf("l")` → 3 |
| `equals(String)` | Content equality | `boolean` | `"Hello".equals("Hello")` → true |
| `equalsIgnoreCase()` | Case-insensitive equality | `boolean` | `"Hello".equalsIgnoreCase("hello")` → true |
| `startsWith(String)` | Starts with prefix | `boolean` | `"hello".startsWith("he")` → true |
| `endsWith(String)` | Ends with suffix | `boolean` | `"hello".endsWith("lo")` → true |
| `contains(CharSequence)` | Contains subsequence | `boolean` | `"hello".contains("ell")` → true |
| `replace(char,char)` | Replace all occurrences | `String` | `"hello".replace('l','p')` → "heppo" |
| `toLowerCase()` | Convert to lowercase | `String` | `"HELLO".toLowerCase()` → "hello" |
| `toUpperCase()` | Convert to uppercase | `String` | `"hello".toUpperCase()` → "HELLO" |
| `trim()` | Remove leading/trailing whitespace | `String` | `"  hello  ".trim()` → "hello" |
| `split(String)` | Split by regex | `String[]` | `"a,b,c".split(",")` → ["a","b","c"] |
| `concat(String)` | Append string | `String` | `"hello".concat(" world")` → "hello world" |

![Common String methods visual guide](https://pplx-res.cloudinary.com/image/upload/v1/java-core/string-methods-cheatsheet.png)

## Performance Comparison
Using String concatenation in loops creates multiple objects, leading to high memory usage and GC pressure.

```java
// ❌ BAD - Creates n+1 objects
String s = "";
for(int i=0; i<1000; i++) {
    s += "a";  // New String each iteration
}

// ✅ GOOD - Efficient
StringBuilder sb = new StringBuilder();
for(int i=0; i<1000; i++) {
    sb.append("a");
}
String result = sb.toString();
```

**StringBuilder is ~10-100x faster** for heavy concatenation.

![String concatenation performance comparison](https://pplx-res.cloudinary.com/image/upload/v1/java-core/string-performance-graph.png)

## Best Practices
- ✅ Use **String literals** or pool for constants
- ✅ Use **StringBuilder** for single-threaded modifications
- ✅ Use **StringBuffer** only for multi-threaded needs
- ✅ Prefer `StringBuilder.append()` over `+` in loops
- ✅ Use `String.format()` or `StringBuilder` for formatted strings
- ✅ Leverage `String.join()` for collections (Java 8+)
- ✅ Intern strings with `intern()` for memory savings (carefully)

## Code Examples

### Basic Usage
```java
public class StringDemo {
    public static void main(String[] args) {
        String str = "Hello World";
        System.out.println("Length: " + str.length());  // 11
        System.out.println("Substring: " + str.substring(0,5));  // Hello
        
        StringBuilder sb = new StringBuilder("Hello");
        sb.append(" World");  // Modifies in-place
        System.out.println(sb.toString());  // Hello World
    }
}
```

---

# Intermediate Java: Core APIs - Arrays

## Introduction to Arrays
Arrays in Java are **fixed-size, homogeneous** data structures that store multiple values of the same type. They are **objects** stored on the heap with a **public final length field**. Arrays provide **O(1) random access** via indices starting from 0.

![Java arrays memory layout](https://pplx-res.cloudinary.com/image/upload/v1/java-core/arrays-memory-diagram.png)

Arrays are fundamental for collections, matrices, and tabular data.

## Array Declaration and Initialization
**Declaration:** `type[] arrayName;` or `type arrayName[];`

**Initialization:**
```java
int[] arr = new int;           // Size 5, default 0[5]
int[] arr = {1, 2, 3, 4, 5};     // Anonymous array
int[] arr = new int[]{1, 2, 3};  // Explicit anonymous
```

**Access:** `arr[0]`, `arr.length` for size.

## Single-Dimensional Arrays
Single-dimensional arrays are **linear collections** storing elements in contiguous memory locations for fast access.

```java
int[] numbers = new int;[5]
for(int i=0; i<numbers.length; i++) {
    numbers[i] = i * 2;
}
```

![Single dimensional array visualization](https://pplx-res.cloudinary.com/image/upload/v1/java-core/single-dim-array.png)

**Length is fixed** after creation; use ArrayList for dynamic sizing.

## Multi-Dimensional Arrays
Multi-dimensional arrays simulate **matrices** or **tables**. Java implements them as **arrays of arrays**.

**2D Declaration:** `int[][] matrix = new int[3][4];`

**Initialization:**
```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

**Access:** `matrix[row][col]`

![2D array matrix visualization](https://pplx-res.cloudinary.com/image/upload/v1/java-core/2d-array-matrix.png)

## Jagged Arrays
**Jagged arrays** have rows of **varying lengths** (arrays of arrays). They save memory for irregular data.

```java
int[][] jagged = new int[];[3]
jagged = new int[]{1, 2};
jagged = new int[]{3, 4, 5};[1]
jagged = new int[]{6};[2]
```

![Jagged array visualization](https://pplx-res.cloudinary.com/image/upload/v1/java-core/jagged-array.png)

Useful for **sparse matrices** or varying data sizes.

## Accessing Array Elements
- **Read:** `int value = arr[index];`
- **Write:** `arr[index] = value;`
- **Length:** `arr.length`
- **Iteration:** `for(int num : arr)` or traditional for loop

**Always check bounds:** `if(index >= 0 && index < arr.length)`

## Arrays Utility Class
`java.util.Arrays` provides **static utility methods** for array operations like sorting, searching, and comparison.

**Import:** `import java.util.Arrays;`

**Key benefits:** Simplified common tasks, optimized implementations.

![Arrays utility class methods](https://pplx-res.cloudinary.com/image/upload/v1/java-core/arrays-utility-methods.png)

## Common Arrays Methods

| Method | Description | Example |
|--------|-------------|---------|
| `toString(array)` | String representation | `Arrays.toString(arr)` → "[1, 2, 3]" |
| `deepToString(array)` | For multi-D arrays | `Arrays.deepToString(matrix)` |
| `sort(array)` | Ascending sort | `Arrays.sort(numbers);` |
| `parallelSort(array)` | Parallel sort (large arrays) | `Arrays.parallelSort(largeArr);` |
| `binarySearch(array, key)` | Search sorted array | `Arrays.binarySearch(sorted, 5)` |
| `fill(array, value)` | Fill all with value | `Arrays.fill(arr, 0);` |
| `equals(array1, array2)` | Content equality | `Arrays.equals(a, b)` |
| `copyOf(array, newLength)` | Copy/resize | `Arrays.copyOf(arr, 10);` |

## Performance Considerations
- **Arrays**: O(1) random access
- **Sorting**: O(n log n) via dual-pivot quicksort (Java 7+)
- **Binary search**: O(log n) on sorted arrays
- **Prefer primitive arrays** over wrapper arrays
- **Use ArrayList** for dynamic sizes
- **`parallelSort()`** for arrays > 10k elements

## Best Practices
- ✅ Use **enhanced for-loop** for iteration
- ✅ **Validate indices** before access
- ✅ **Sort before binarySearch**
- ✅ Use `toString()` for debugging
- ✅ Prefer `Arrays.copyOf()` over `System.arraycopy()`
- ✅ **Initialize with defaults** via `fill()`
- ✅ Use **ArrayList** for dynamic sizes

## Code Examples

### Single-Dimensional Array
```java
import java.util.Arrays;

public class ArrayDemo {
    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};
        System.out.println("Original: " + Arrays.toString(arr));
        
        Arrays.sort(arr);
        System.out.println("Sorted: " + Arrays.toString(arr));
        
        int key = 22;
        int index = Arrays.binarySearch(arr, key);
        System.out.println("Index of " + key + ": " + index);
    }
}
```

### Multi-Dimensional Array
```java
import java.util.Arrays;

public class MatrixDemo {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        
        System.out.println(Arrays.deepToString(matrix));
        
        int sum = 0;
        for(int i=0; i<matrix.length; i++) {
            sum += matrix[i][i];
        }
        System.out.println("Diagonal sum: " + sum);  // 15
    }
}
```

### Jagged Array (Fixed)
```java
import java.util.Arrays;

public class JaggedDemo {
    public static void main(String[] args) {
        int[][] jagged = new int[];[3]
        jagged = new int[]{1, 2};
        jagged = new int[]{3, 4, 5};[1]
        jagged = new int[]{6};[2]
        
        for(int[] row : jagged) {
            System.out.println("Row length: " + row.length + " - " + Arrays.toString(row));
        }
    }
}
```
