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

![Java Strings Overview](https://www.geeksforgeeks.org/wp-content/uploads/Strings1.png)

## String Immutability
Java Strings are immutable, meaning once created, their value cannot be changed. Any modification operation like concat() or replace() creates a new String object, leaving the original unchanged. This design ensures thread-safety and allows String objects to be cached in the String pool.

![String Immutability Diagram](https://javainsimpleway.com/wp-content/uploads/2020/05/string-immutability-300x252.png)

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

![Comparison Chart](https://www.geeksforgeeks.org/wp-content/uploads/string-vs-stringbuilder-vs-stringbuffer.png)

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

![String Methods Infographic](https://www.w3schools.com/java/java_ref_string.asp/image_string_methods.png)

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

![Performance Graph](https://www.baeldung.com/wp-content/uploads/2017/07/string-concatenation.png)

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

These notes cover essential String handling for Java applications. Practice with code examples to master performance implications.
