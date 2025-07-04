# 🌟 Strings: The Art of Text Processing

---

## 🚀 Why Learn Strings?

Imagine a necklace with beads, where each bead represents a character. You can read the beads from left to right to form words, sentences, or even entire stories! This is the magic of **strings**—the most fundamental way to handle text in programming.

Strings are everywhere: user input, file processing, web development, data analysis, and more. Mastering string manipulation unlocks your ability to build real-world applications that work with text data.

---

## 🧩 What is a String? (With Visuals)

A **string** is a sequence of characters stored in contiguous memory locations. Think of it as an array of characters, but with special properties and operations designed for text processing.

### 📦 Analogy: A Beaded Necklace

```
┌────┬────┬────┬────┬────┬────┬────┬────┬────┬────┬────┐
│ H  │ e  │ l  │ l  │ o  │    │ W  │ o  │ r  │ l  │ d  │
└────┴────┴────┴────┴────┴────┴────┴────┴────┴────┴────┘
   0    1    2    3    4    5    6    7    8    9   10   ← Index
```

- Each bead is a **character** (letter, number, symbol, or space)
- The position number is the **index** (starts at 0)
- You can read the necklace from left to right to form words

### 🧠 Key Properties
- **Immutable** (in most languages) - once created, cannot be changed
- **Zero-based indexing** - first character is at index 0
- **Length** - number of characters in the string
- **Character encoding** - typically ASCII or Unicode

### 💡 Real-World Examples
- User names and passwords
- Email addresses and URLs
- File paths and document content
- JSON data and API responses

---

## 🏷️ Types of Strings

Strings come in different flavors! Let's explore the various types and their characteristics.

### 1. String Literals
- **Direct text**: Written directly in code with quotes
- **Analogy**: Writing a note on paper

```java
String message = "Hello World";
String empty = "";
String single = "A";
```

### 2. String Objects
- **Created using new**: Explicit object creation
- **Analogy**: Building a custom sign

```java
String str1 = new String("Hello");
char[] chars = {'H', 'e', 'l', 'l', 'o'};
String str2 = new String(chars);
```

### 3. StringBuffer vs StringBuilder
- **Mutable strings**: Can be changed after creation
- **Analogy**: Whiteboard vs paper

```
StringBuffer: Thread-safe, slower
StringBuilder: Not thread-safe, faster
```

### 4. Character Arrays
- **Raw character data**: Most basic form
- **Analogy**: Individual beads before stringing

```java
char[] charArray = {'H', 'e', 'l', 'l', 'o'};
```

---

### ⚡ Quick Comparison Table

| Type           | Mutable | Thread-Safe | Performance | Use Case                    |
|----------------|---------|-------------|-------------|----------------------------|
| String         | No      | Yes         | Medium      | General text storage        |
| StringBuffer   | Yes     | Yes         | Slow        | Multi-threaded apps         |
| StringBuilder  | Yes     | No          | Fast        | Single-threaded apps        |
| char[]         | Yes     | No          | Fastest     | Low-level operations        |

---

### 🕵️‍♂️ When to Use Which?
- **String**: For most text operations, when you don't need to modify
- **StringBuilder**: When you need to build strings efficiently
- **StringBuffer**: When you need thread safety
- **char[]**: For performance-critical operations

---

## 🛠️ Core String Operations (With Visuals & Code)

Strings are powerful because you can do so much with them! Here are the most important operations, explained step by step.

---

### 1. Access (Read)
- **What?** Get a character at a specific index.
- **Analogy:** Reading a specific bead on the necklace.

```
String: "Hello World"
Index:    0  1  2  3  4  5  6  7  8  9  10

To access the 4th character (index 3):

      "Hello World"
           ↑
         str.charAt(3) = 'l'
```

**Code:**
```java
String str = "Hello World";
char firstChar = str.charAt(0); // 'H'
char lastChar = str.charAt(str.length() - 1); // 'd'
```
```python
str = "Hello World"
first_char = str[0]  # 'H'
last_char = str[-1]  # 'd'
```
```cpp
string str = "Hello World";
char firstChar = str[0]; // 'H'
char lastChar = str[str.length() - 1]; // 'd'
```

---

### 2. Concatenation
- **What?** Join two or more strings together.
- **Analogy:** Connecting two necklaces to make a longer one.

```
String 1: "Hello"
String 2: "World"

Result: "Hello" + " " + "World" = "Hello World"
```

**Code:**
```java
String str1 = "Hello";
String str2 = "World";
String result = str1 + " " + str2; // "Hello World"
```
```python
str1 = "Hello"
str2 = "World"
result = str1 + " " + str2  # "Hello World"
```
```cpp
string str1 = "Hello";
string str2 = "World";
string result = str1 + " " + str2; // "Hello World"
```

---

### 3. Substring
- **What?** Extract a portion of a string.
- **Analogy:** Cutting a section of the necklace.

```
String: "Hello World"
Substring(0, 5): "Hello"
Substring(6): "World"
```

**Code:**
```java
String str = "Hello World";
String sub1 = str.substring(0, 5); // "Hello"
String sub2 = str.substring(6); // "World"
```
```python
str = "Hello World"
sub1 = str[0:5]  # "Hello"
sub2 = str[6:]   # "World"
```
```cpp
string str = "Hello World";
string sub1 = str.substr(0, 5); // "Hello"
string sub2 = str.substr(6); // "World"
```

---

### 4. Search
- **What?** Find the position of a character or substring.
- **Analogy:** Looking for a specific bead or pattern on the necklace.

```
String: "Hello World Hello Java"
Search for "Hello":

"Hello World Hello Java"
 ↑                    ↑
First occurrence      Second occurrence
at index 0           at index 12
```

**Code:**
```java
String str = "Hello World Hello Java";
int firstIndex = str.indexOf("Hello"); // 0
int lastIndex = str.lastIndexOf("Hello"); // 12
boolean contains = str.contains("World"); // true
```
```python
str = "Hello World Hello Java"
first_index = str.find("Hello")  # 0
last_index = str.rfind("Hello")  # 12
contains = "World" in str  # True
```
```cpp
string str = "Hello World Hello Java";
size_t firstIndex = str.find("Hello"); // 0
size_t lastIndex = str.rfind("Hello"); // 12
bool contains = str.find("World") != string::npos; // true
```

---

### 5. Replace
- **What?** Replace characters or substrings with new ones.
- **Analogy:** Swapping beads on the necklace.

```
Original: "Hello World"
Replace "World" with "Java":

"Hello World" → "Hello Java"
```

**Code:**
```java
String str = "Hello World";
String replaced = str.replace("World", "Java"); // "Hello Java"
```
```python
str = "Hello World"
replaced = str.replace("World", "Java")  # "Hello Java"
```
```cpp
string str = "Hello World";
size_t pos = str.find("World");
if (pos != string::npos) {
    str.replace(pos, 5, "Java"); // "Hello Java"
}
```

---

### ⏱️ Time Complexity Summary

| Operation    | Time Complexity |
|--------------|----------------|
| Access       | O(1)           |
| Concatenation| O(n)           |
| Substring    | O(n)           |
| Search       | O(n)           |
| Replace      | O(n)           |
| Length       | O(1)           |

---

## 💡 Example 1: Basic String Operations

### Problem Statement
Demonstrate basic string operations: creation, access, modification, and traversal.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  String Operations Demo                                │
│                                                       │
│  Step 1: Create string                                │
│  "Hello World" ← String literal                       │
│                                                       │
│  Step 2: Access characters                            │
│  str[0] = 'H', str[1] = 'e', str[4] = 'o'            │
│                                                       │
│  Step 3: Get length                                   │
│  Length = 11 characters                               │
│                                                       │
│  Step 4: Get substring                                │
│  substring(0, 5) = "Hello"                            │
│  substring(6) = "World"                               │
│                                                       │
│  Step 5: Find character                               │
│  indexOf('o') = 4 (first occurrence)                  │
│  lastIndexOf('o') = 7 (last occurrence)               │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
public class StringBasics {
    public static void main(String[] args) {
        // 1. String Creation
        String str1 = "Hello World";
        String str2 = new String("Hello World");
        char[] charArray = {'H', 'e', 'l', 'l', 'o'};
        String str3 = new String(charArray);
        
        System.out.println("String 1: " + str1);
        System.out.println("String 2: " + str2);
        System.out.println("String 3: " + str3);
        
        // 2. String Length
        System.out.println("Length of str1: " + str1.length());
        
        // 3. Character Access
        System.out.println("First character: " + str1.charAt(0));
        System.out.println("Last character: " + str1.charAt(str1.length() - 1));
        
        // 4. String Comparison
        System.out.println("str1 equals str2: " + str1.equals(str2));
        System.out.println("str1 == str2: " + (str1 == str2)); // Reference comparison
        
        // 5. String Concatenation
        String firstName = "John";
        String lastName = "Doe";
        String fullName = firstName + " " + lastName;
        System.out.println("Full name: " + fullName);
        
        // 6. Substring Operations
        String sub1 = str1.substring(0, 5); // "Hello"
        String sub2 = str1.substring(6); // "World"
        System.out.println("Substring 1: " + sub1);
        System.out.println("Substring 2: " + sub2);
        
        // 7. String Search
        System.out.println("Index of 'o': " + str1.indexOf('o'));
        System.out.println("Last index of 'o': " + str1.lastIndexOf('o'));
        System.out.println("Contains 'World': " + str1.contains("World"));
        
        // 8. String Traversal
        System.out.println("Traversing string:");
        for (int i = 0; i < str1.length(); i++) {
            System.out.print(str1.charAt(i) + " ");
        }
        System.out.println();
        
        // 9. String Methods
        System.out.println("Uppercase: " + str1.toUpperCase());
        System.out.println("Lowercase: " + str1.toLowerCase());
        System.out.println("Trimmed: " + "  Hello  ".trim());
        System.out.println("Replaced: " + str1.replace("World", "Java"));
    }
}
```

## 💡 Example 2: String Manipulation

### Problem Statement
Demonstrate advanced string manipulation techniques.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  String Manipulation                                  │
│                                                       │
│  Original: "  Hello World  "                          │
│                                                       │
│  Step 1: Trim whitespace                              │
│  "Hello World" ← Removed leading/trailing spaces      │
│                                                       │
│  Step 2: Split by space                               │
│  ["Hello", "World"] ← Array of substrings             │
│                                                       │
│  Step 3: Join with delimiter                          │
│  "Hello-World" ← Joined with "-"                      │
│                                                       │
│  Step 4: Replace characters                           │
│  "Hello Java" ← Replaced "World" with "Java"          │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
import java.util.*;

public class StringManipulation {
    public static void main(String[] args) {
        String text = "  Hello World, Welcome to Java Programming  ";
        
        System.out.println("Original: '" + text + "'");
        
        // 1. Trim whitespace
        String trimmed = text.trim();
        System.out.println("After trim: '" + trimmed + "'");
        
        // 2. Split string
        String[] words = trimmed.split(" ");
        System.out.println("Split words:");
        for (String word : words) {
            System.out.println("  - " + word);
        }
        
        // 3. Join strings
        String joined = String.join("-", words);
        System.out.println("Joined with '-': " + joined);
        
        // 4. Replace operations
        String replaced = text.replace("World", "Java");
        System.out.println("After replace: " + replaced);
        
        String replacedAll = text.replaceAll("\\s+", " "); // Replace multiple spaces
        System.out.println("After replaceAll: '" + replacedAll + "'");
        
        // 5. Case operations
        System.out.println("Uppercase: " + text.toUpperCase());
        System.out.println("Lowercase: " + text.toLowerCase());
        
        // 6. Check string properties
        System.out.println("Starts with 'Hello': " + text.trim().startsWith("Hello"));
        System.out.println("Ends with 'Programming': " + text.trim().endsWith("Programming"));
        System.out.println("Is empty: " + text.isEmpty());
        System.out.println("Is blank: " + text.isBlank());
        
        // 7. String formatting
        String name = "John";
        int age = 25;
        String formatted = String.format("Name: %s, Age: %d", name, age);
        System.out.println("Formatted: " + formatted);
        
        // 8. StringBuilder for efficient concatenation
        StringBuilder sb = new StringBuilder();
        sb.append("Hello");
        sb.append(" ");
        sb.append("World");
        sb.append("!");
        String result = sb.toString();
        System.out.println("StringBuilder result: " + result);
    }
}
```

## 💡 Example 3: String Pattern Matching

### Problem Statement
Implement basic pattern matching algorithms.

### Visual Walkthrough

```
┌─────────────────────────────────────────────────────────┐
│  Pattern Matching                                     │
│                                                       │
│  Text:    "Hello World Hello Java"                    │
│  Pattern: "Hello"                                     │
│                                                       │
│  Step 1: Find first occurrence                        │
│  "Hello World Hello Java"                             │
│   ↑                                                   │
│   Found at index 0                                    │
│                                                       │
│  Step 2: Find next occurrence                         │
│  "Hello World Hello Java"                             │
│              ↑                                        │
│              Found at index 12                        │
│                                                       │
│  Step 3: Count all occurrences                        │
│  Total occurrences: 2                                 │
└─────────────────────────────────────────────────────────┘
```

### Java Implementation

```java
public class StringPatternMatching {
    
    // Simple pattern matching
    public static int findPattern(String text, String pattern) {
        if (text == null || pattern == null || pattern.length() > text.length()) {
            return -1;
        }
        
        for (int i = 0; i <= text.length() - pattern.length(); i++) {
            boolean found = true;
            for (int j = 0; j < pattern.length(); j++) {
                if (text.charAt(i + j) != pattern.charAt(j)) {
                    found = false;
                    break;
                }
            }
            if (found) {
                return i;
            }
        }
        return -1;
    }
    
    // Count pattern occurrences
    public static int countPattern(String text, String pattern) {
        if (text == null || pattern == null || pattern.length() > text.length()) {
            return 0;
        }
        
        int count = 0;
        int index = 0;
        
        while ((index = text.indexOf(pattern, index)) != -1) {
            count++;
            index += 1; // Move to next position
        }
        
        return count;
    }
    
    // Check if string is palindrome
    public static boolean isPalindrome(String str) {
        if (str == null) {
            return false;
        }
        
        int left = 0;
        int right = str.length() - 1;
        
        while (left < right) {
            if (str.charAt(left) != str.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        
        return true;
    }
    
    // Reverse string
    public static String reverse(String str) {
        if (str == null) {
            return null;
        }
        
        StringBuilder sb = new StringBuilder(str);
        return sb.reverse().toString();
    }
    
    // Remove duplicates from string
    public static String removeDuplicates(String str) {
        if (str == null) {
            return null;
        }
        
        StringBuilder result = new StringBuilder();
        boolean[] seen = new boolean[256]; // ASCII characters
        
        for (char c : str.toCharArray()) {
            if (!seen[c]) {
                result.append(c);
                seen[c] = true;
            }
        }
        
        return result.toString();
    }
    
    public static void main(String[] args) {
        String text = "Hello World Hello Java";
        String pattern = "Hello";
        
        // Pattern matching
        int index = findPattern(text, pattern);
        System.out.println("Pattern '" + pattern + "' found at index: " + index);
        
        int count = countPattern(text, pattern);
        System.out.println("Pattern '" + pattern + "' appears " + count + " times");
        
        // Palindrome check
        String[] testStrings = {"racecar", "hello", "A man a plan a canal Panama", ""};
        for (String test : testStrings) {
            System.out.println("'" + test + "' is palindrome: " + isPalindrome(test));
        }
        
        // String reverse
        String original = "Hello World";
        String reversed = reverse(original);
        System.out.println("Original: " + original);
        System.out.println("Reversed: " + reversed);
        
        // Remove duplicates
        String withDuplicates = "hello world";
        String withoutDuplicates = removeDuplicates(withDuplicates);
        System.out.println("With duplicates: " + withDuplicates);
        System.out.println("Without duplicates: " + withoutDuplicates);
    }
}
```

## 🎯 Common String Patterns

### Pattern 1: Two Pointers
**Use case:** When you need to compare characters from opposite ends.

```
String: "racecar"
       ↑     ↑
     left  right
```

**Code:**
```java
public boolean isPalindrome(String s) {
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

### Pattern 2: Sliding Window
**Use case:** When you need to find substrings with specific properties.

```
String: "abcabcbb"
Window: "abc" → "bca" → "cab" → "abc"
```

**Code:**
```java
public int lengthOfLongestSubstring(String s) {
    Set<Character> set = new HashSet<>();
    int maxLength = 0;
    int left = 0;
    
    for (int right = 0; right < s.length(); right++) {
        while (set.contains(s.charAt(right))) {
            set.remove(s.charAt(left));
            left++;
        }
        set.add(s.charAt(right));
        maxLength = Math.max(maxLength, right - left + 1);
    }
    
    return maxLength;
}
```

### Pattern 3: Character Frequency
**Use case:** When you need to count or compare character occurrences.

```
String: "anagram"
Frequency: a=3, n=1, g=1, r=1, m=1
```

**Code:**
```java
public boolean isAnagram(String s, String t) {
    if (s.length() != t.length()) {
        return false;
    }
    
    int[] freq = new int[26];
    
    for (char c : s.toCharArray()) {
        freq[c - 'a']++;
    }
    
    for (char c : t.toCharArray()) {
        freq[c - 'a']--;
        if (freq[c - 'a'] < 0) {
            return false;
        }
    }
    
    return true;
}
```

---

## 🚀 Practice Problems

### 🟢 Easy Level (10 Problems)
1. **[Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)** - Two pointers approach
2. **[Reverse String](https://leetcode.com/problems/reverse-string/)** - In-place reversal
3. **[Valid Anagram](https://leetcode.com/problems/valid-anagram/)** - Character frequency
4. **[First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)** - Hash map
5. **[Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)** - Horizontal scanning
6. **[Implement strStr()](https://leetcode.com/problems/implement-strstr/)** - String matching
7. **[Count and Say](https://leetcode.com/problems/count-and-say/)** - String generation
8. **[Add Binary](https://leetcode.com/problems/add-binary/)** - Binary string addition
9. **[Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)** - Stack approach
10. **[Roman to Integer](https://leetcode.com/problems/roman-to-integer/)** - Character mapping

### 🟡 Medium Level (10 Problems)
1. **[Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)** - Sliding window
2. **[Group Anagrams](https://leetcode.com/problems/group-anagrams/)** - Hash map with sorting
3. **[Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)** - Expand around center
4. **[String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/)** - Character parsing
5. **[Integer to Roman](https://leetcode.com/problems/integer-to-roman/)** - Greedy approach
6. **[ZigZag Conversion](https://leetcode.com/problems/zigzag-conversion/)** - Pattern simulation
7. **[Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)** - Sliding window
8. **[Reorganize String](https://leetcode.com/problems/reorganize-string/)** - Greedy with heap
9. **[Decode String](https://leetcode.com/problems/decode-string/)** - Stack approach
10. **[Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/)** - String parsing

### 🔴 Hard Level (5 Problems)
1. **[Regular Expression Matching](https://leetcode.com/problems/regular-expression-matching/)** - Dynamic programming
2. **[Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)** - Sliding window with frequency
3. **[Word Ladder](https://leetcode.com/problems/word-ladder/)** - BFS with string transformation
4. **[Word Ladder II](https://leetcode.com/problems/word-ladder-ii/)** - BFS with path tracking
5. **[Longest Valid Parentheses](https://leetcode.com/problems/longest-valid-parentheses/)** - Stack or DP

---

## 🐛 Debugging & Common Pitfalls

### ❌ Common Mistakes

1. **String Comparison with ==**
   ```java
   String str1 = "Hello";
   String str2 = new String("Hello");
   boolean wrong = str1 == str2; // False! Use equals()
   boolean correct = str1.equals(str2); // True
   ```

2. **Forgetting String Immutability**
   ```java
   String str = "Hello";
   str.toUpperCase(); // This doesn't change str!
   str = str.toUpperCase(); // Correct way
   ```

3. **Inefficient String Concatenation**
   ```java
   // Bad: Creates new string each iteration
   String result = "";
   for (int i = 0; i < 1000; i++) {
       result += i; // O(n²) time complexity
   }
   
   // Good: Use StringBuilder
   StringBuilder sb = new StringBuilder();
   for (int i = 0; i < 1000; i++) {
       sb.append(i); // O(n) time complexity
   }
   ```

### 🔧 Debugging Tips

1. **Print String Properties**
   ```java
   System.out.println("Length: " + str.length());
   System.out.println("Is empty: " + str.isEmpty());
   System.out.println("Contains 'x': " + str.contains("x"));
   ```

2. **Check for Null and Empty**
   ```java
   if (str != null && !str.isEmpty()) {
       // Safe to process string
   }
   ```

3. **Use Debugger**
   - Set breakpoints in string operations
   - Watch string values change
   - Step through character-by-character

---

## 🧠 Memory & Performance

### How Strings Work in Memory

```
Memory Layout:
┌─────────────────────────────────────────┐
│  String Pool (for literals)            │
│  "Hello" ← Shared reference            │
│  "World" ← Shared reference            │
│                                       │
│  Heap (for new String())              │
│  [H][e][l][l][o] ← Individual object  │
└─────────────────────────────────────────┘
```

- **String Pool**: Shared storage for string literals
- **Heap**: Individual storage for new String() objects
- **Immutable**: Once created, strings cannot be modified

### Performance Considerations

| Operation | Best Case | Worst Case | Space |
|-----------|-----------|------------|-------|
| Access    | O(1)      | O(1)       | O(1)  |
| Concatenation| O(1)    | O(n)       | O(n)  |
| Substring | O(1)      | O(n)       | O(n)  |
| Search    | O(1)      | O(n)       | O(1)  |

---

## 🎨 Key Takeaways

### ✅ Do's:
- Always check for null strings before operations
- Use appropriate string methods for efficiency
- Consider immutability when concatenating strings
- Handle edge cases (empty strings, single characters)
- Use StringBuilder for multiple concatenations
- Validate input strings before processing

### ❌ Don'ts:
- Don't use == for string comparison (use equals())
- Don't concatenate strings in loops (use StringBuilder)
- Don't forget to handle case sensitivity
- Don't ignore character encoding issues
- Don't forget string immutability
- Don't use string operations for performance-critical code

### 🧠 Memory Aids:
- **"Strings are immutable"**
- **"Use equals() not == for comparison"**
- **"StringBuilder for multiple concatenations"**
- **"Index starts at 0"**
- **"Length vs size confusion"**

---

## 🔍 Debugging Tips

1. **Check string length** - Always verify if string is empty
2. **Print string contents** - Use helper methods to visualize
3. **Use debugger** - Step through string operations
4. **Test with edge cases** - Empty strings, single characters, special characters
5. **Validate input** - Check for null strings and invalid indices
6. **Check character encoding** - Be aware of Unicode issues

---

## 📚 Further Reading

- [GeeksforGeeks - Strings](https://www.geeksforgeeks.org/string-data-structure/)
- [LeetCode - String Problems](https://leetcode.com/tag/string/)
- [HackerRank - String Problems](https://www.hackerrank.com/domains/algorithms?filters%5Bsubdomains%5D%5B%5D=strings)
- [Codeforces - String Problems](https://codeforces.com/problemset?tags=strings)

---

**🎉 Congratulations!** You've mastered Strings. Practice with the problems above to solidify your understanding!

---

**[← Back to DSA Concepts](../README.md)** | **[Previous Topic →](04 - Queues.md)** 