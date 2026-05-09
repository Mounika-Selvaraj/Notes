# Intermediate Java: Core APIs - Strings

## Table of Contents
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

## Introduction to Strings
Strings are fundamental in Java for handling text data. They represent sequences of characters and are used everywhere from user input to configuration files. Java provides three main classes for string manipulation: String, StringBuilder, and StringBuffer.

[image:47]

## String Immutability
Java Strings are immutable, meaning once created, their value cannot be changed. Any modification operation like concat() or replace() creates a new String object, leaving the original unchanged. This design ensures thread-safety and allows String objects to be cached in the String pool.

[image:49]

Immutability provides security benefits as Strings are used in class loading and cannot be altered maliciously.

## String vs StringBuilder vs StringBuffer

| Feature | String | StringBuilder | StringBuffer |
|---------|--------|---------------|--------------|
| Mutability | Immutable | Mutable | Mutable |
| Thread-Safety | Yes (due to immutability) | No | Yes (synchronized methods) |
| Performance | Slow for repeated modifications | Fastest | Slower than StringBuilder |
| Introduced In | Java 1.0 | Java 1.5 | Java 1.0 |
| Memory Usage | Creates new objects | Modifies in-place | Modifies in-place |
| Use Case | Fixed text | Single-threaded concatenation | Multi-threaded concatenation |

StringBuilder (since Java 5) replaced StringBuffer in most cases due to better performance in single-threaded environments.

[image:55]

## String Class
The String class is final and represents constant sequences of characters. It uses a char[] array internally but is immutable. Strings are stored in a pool for reuse.

Key characteristics:
- Created via literals: `String s = "Hello";`
- Methods return new Strings
- HashCode is cached for performance

## StringBuilder Class
StringBuilder is mutable and not thread-safe, making it faster than StringBuffer. It's ideal for string manipulations in single-threaded code. Introduced in Java 5 as a modern alternative.

Main methods: `append()`, `insert()`, `delete()`, `reverse()`.

## StringBuffer Class
StringBuffer is similar to StringBuilder but thread-safe due to synchronized methods. Use it only when thread safety is required. It's legacy but still used in multi-threaded scenarios.

All mutating methods are synchronized, adding overhead.

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
| `join(CharSequence, Iterable)` | Join with delimiter | `String` | `String.join(", ", "a","b")` → "a, b" |

[image:57]

## Performance Comparison
Using String concatenation in loops creates multiple objects, leading to high memory usage and GC pressure.

```java
// BAD - Creates n+1 objects
String s = "";
for(int i=0; i<1000; i++) {
    s += "a";  // New String each iteration
}

// GOOD - Efficient
StringBuilder sb = new StringBuilder();
for(int i=0; i<1000; i++) {
    sb.append("a");
}
String result = sb.toString();
```

StringBuilder is ~10-100x faster for heavy concatenation.

[image:51]

## Best Practices
- Use String literals or pool for constants
- Use StringBuilder for single-threaded modifications
- Use StringBuffer only for multi-threaded needs
- Prefer `StringBuilder.append()` over `+` in loops
- Use `String.format()` or `StringBuilder` for formatted strings
- Leverage `String.join()` for collections (Java 8+)
- Intern strings with `intern()` for memory savings (carefully)

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

### StringBuilder vs String Concatenation
```java
public class PerformanceDemo {
    public static void main(String[] args) {
        long start = System.currentTimeMillis();
        
        // String concatenation (slow)
        String s = "";
        for(int i = 0; i < 10000; i++) {
            s += i;
        }
        System.out.println("String concat: " + (System.currentTimeMillis() - start) + "ms");
        
        // StringBuilder (fast)
        start = System.currentTimeMillis();
        StringBuilder sb = new StringBuilder();
        for(int i = 0; i < 10000; i++) {
            sb.append(i);
        }
        String result = sb.toString();
        System.out.println("StringBuilder: " + (System.currentTimeMillis() - start) + "ms");
    }
}
```

### Thread-Safe Example
```java
// Multi-threaded - Use StringBuffer
StringBuffer sbf = new StringBuffer();
ExecutorService executor = Executors.newFixedThreadPool(4);
for(int i=0; i<4; i++) {
    executor.submit(() -> sbf.append(Thread.currentThread().getName()));
}
executor.shutdown();
```
# Intermediate Java: Core APIs - Arrays

## Table of Contents
- [Introduction to Arrays](#introduction-to-arrays)
- [Declaring and Initializing Arrays](#declaring-and-initializing-arrays)
- [Single-Dimensional Arrays](#single-dimensional-arrays)
- [Multi-Dimensional Arrays](#multi-dimensional-arrays)
- [Jagged Arrays](#jagged-arrays)
- [Array Memory Layout](#array-memory-layout)
- [Array Utilities - Arrays Class](#array-utilities---arrays-class)
- [Common Arrays Methods](#common-arrays-methods)
- [Performance Tips](#performance-tips)
- [Code Examples](#code-examples)

## Introduction to Arrays
Arrays in Java are fixed-size, homogeneous data structures that store multiple values of the same type. They are objects stored on the heap with a public final length field. Arrays provide efficient random access via indices starting from 0.

[image:88]

Arrays are fundamental for collections, matrices, and tabular data.

## Declaring and Initializing Arrays
**Declaration:** `type[] arrayName;` or `type arrayName[];`

**Initialization:**
- `int[] arr = new int[5];` // Size 5, default 0
- `int[] arr = {1, 2, 3, 4, 5};` // Anonymous array
- `int[] arr = new int[]{1, 2, 3};`

Access: `arr[0]`, `arr.length` for size.

## Single-Dimensional Arrays
Single-dimensional arrays are linear collections. They store elements in contiguous memory locations for fast access.

Example:
```java
int[] numbers = new int;
for(int i=0; i<numbers.length; i++) {
    numbers[i] = i * 2;
}
```

[image:104]

Length is fixed after creation; use ArrayList for dynamic sizing.

## Multi-Dimensional Arrays
Multi-dimensional arrays simulate matrices or tables. Java implements them as arrays of arrays.

**2D Declaration:** `int[][] matrix = new int[3][4];`

**Initialization:**
```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

Access: `matrix[row][col]`

[image:85]

Supports 3D+: `int[][][] cube = new int[2][3][4];`

## Jagged Arrays
Jagged arrays have rows of varying lengths (arrays of arrays). They save memory for irregular data.

```java
int[][] jagged = new int[];
jagged = new int[]{1, 2};
jagged = new int[]{3, 4, 5};[1]
jagged = new int[]{6};[2]
```

[image:98]

Useful for sparse matrices or varying data sizes.

## Array Memory Layout
Arrays are heap objects. The reference is on stack, array object on heap with length field and element data.

- Stack: reference variable
- Heap: Array object (length + char[]/int[] data)

[image:97]

All elements initialized to 0/false/null by default.

## Array Utilities - Arrays Class
`java.util.Arrays` provides static utility methods for array operations like sorting, searching, and comparison.

Import: `import java.util.Arrays;`

Key benefits: Simplified common tasks, optimized implementations.

[image:81]

## Common Arrays Methods

| Method | Description | Example |
|--------|-------------|---------|
| `toString(array)` | String representation | `Arrays.toString(arr)` → "[1, 2, 3]" |
| `deepToString(array)` | For multi-D arrays | `Arrays.deepToString(matrix)` |
| `sort(array)` | Ascending sort | `Arrays.sort(numbers);` |
| `parallelSort(array)` | Parallel sort (large arrays) | `Arrays.parallelSort(largeArr);` |
| `binarySearch(array, key)` | Search sorted array (returns index or negative) | `Arrays.binarySearch(sorted, 5)` |
| `fill(array, value)` | Fill all with value | `Arrays.fill(arr, 0);` |
| `fill(array, from, to, value)` | Partial fill | `Arrays.fill(arr, 1, 3, 99);` |
| `equals(array1, array2)` | Content equality | `Arrays.equals(a, b)` |
| `deepEquals(array1, array2)` | For multi-D | `Arrays.deepEquals(m1, m2)` |
| `copyOf(array, newLength)` | Copy/resize | `Arrays.copyOf(arr, 10);` |
| `copyOfRange(array, from, to)` | Subarray copy | `Arrays.copyOfRange(arr, 1, 4);` |

## Performance Tips
- Use `Arrays.sort()` over manual bubble sort
- `binarySearch()` requires sorted array (O(log n))
- Prefer primitive arrays over wrapper arrays
- For dynamic sizes, use ArrayList
- `parallelSort()` for arrays > 10k elements
- Avoid resizing: estimate size upfront

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
public class MatrixDemo {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        
        // Print using deepToString
        System.out.println(Arrays.deepToString(matrix));
        
        // Sum diagonal
        int sum = 0;
        for(int i=0; i<matrix.length; i++) {
            sum += matrix[i][i];
        }
        System.out.println("Diagonal sum: " + sum);
    }
}
```

### Jagged Array
```java
public class JaggedDemo {
    public static void main(String[] args) {
        int[][] jagged = new int[];
        jagged = new int[]{1, 2, 3};
        jagged = new int[]{4, 5};[1]
        jagged = new int[]{6, 7, 8, 9};[2]
        
        for(int[] row : jagged) {
            System.out.println(Arrays.toString(row));
        }
    }
}
```

### Arrays Utilities
```java
public class ArraysUtilDemo {
    public static void main(String[] args) {
        int[] arr = new int;
        Arrays.fill(arr, 42);
        System.out.println("Filled: " + Arrays.toString(arr));
        
        int[] copy = Arrays.copyOfRange(arr, 1, 4);
        System.out.println("Copy: " + Arrays.toString(copy));
    }
}
```

Master arrays for efficient data handling. Transition to Collections for flexibility.
