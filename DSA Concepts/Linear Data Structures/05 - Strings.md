# 📝 Strings - Text Data Structure

## 📖 What is a String?

Imagine a necklace with beads, where each bead represents a character. You can read the beads from left to right to form words or sentences. That's exactly what a **String** is in programming!

A string is a sequence of characters stored in contiguous memory locations. It's one of the most fundamental and widely used data structures in programming.

```
┌─────────────────────────────────────────────────────────┐
│  String Visualization                                 │
│                                                       │
│  String: "Hello World"                                │
│                                                       │
│  Index:    0    1    2    3    4    5    6    7      │
│           ┌────┬────┬────┬────┬────┬────┬────┬────┐   │
│  Chars:   │ H  │ e  │ l  │ l  │ o  │    │ W  │ o  │   │
│           └────┴────┴────┴────┴────┴────┴────┴────┘   │
│                                                       │
│  Length: 8 characters                                 │
│  Memory: [H][e][l][l][o][ ][W][o][r][l][d]           │
│           ↑   ↑   ↑   ↑   ↑   ↑   ↑   ↑   ↑   ↑   ↑  │
│           Contiguous Character Storage                │
└─────────────────────────────────────────────────────────┘
```

## 🎯 String Properties

### 1. Immutability
Strings are immutable in many languages (Java, Python, C#), meaning once created, they cannot be changed.

### 2. Zero-based Indexing
String characters are accessed using indices starting from 0.

### 3. Length
The number of characters in a string.

### 4. Character Encoding
Strings are typically stored using character encodings like ASCII or Unicode.

## 🧠 String Operations

### 1. Access (Read)
**Time Complexity**: O(1) - Constant time

```java
String str = "Hello World";
char firstChar = str.charAt(0); // 'H'
char lastChar = str.charAt(str.length() - 1); // 'd'
```

### 2. Concatenation
**Time Complexity**: O(n) - Linear time

```java
String str1 = "Hello";
String str2 = "World";
String result = str1 + " " + str2; // "Hello World"
```

### 3. Substring
**Time Complexity**: O(n) - Linear time

```java
String str = "Hello World";
String sub = str.substring(0, 5); // "Hello"
String sub2 = str.substring(6); // "World"
```

### 4. Search
**Time Complexity**: O(n) - Linear time

```java
String str = "Hello World";
int index = str.indexOf("World"); // 6
boolean contains = str.contains("Hello"); // true
```

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

## 🚀 Practice Problems

### 🟢 Easy Level (5 Problems)
1. **[Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)** - Two pointers approach
2. **[Reverse String](https://leetcode.com/problems/reverse-string/)** - In-place reversal
3. **[Valid Anagram](https://leetcode.com/problems/valid-anagram/)** - Character frequency
4. **[First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)** - Hash map
5. **[Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)** - Horizontal scanning

### 🟡 Medium Level (3 Problems)
1. **[Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)** - Sliding window
2. **[Group Anagrams](https://leetcode.com/problems/group-anagrams/)** - Hash map with sorting
3. **[Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)** - Expand around center

### 🔴 Hard Level (2 Problems)
1. **[Regular Expression Matching](https://leetcode.com/problems/regular-expression-matching/)** - Dynamic programming
2. **[Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)** - Sliding window with frequency

## 🎨 Key Takeaways

### ✅ Do's:
- Always check for null strings before operations
- Use appropriate string methods for efficiency
- Consider immutability when concatenating strings
- Handle edge cases (empty strings, single characters)

### ❌ Don'ts:
- Don't use == for string comparison (use equals())
- Don't concatenate strings in loops (use StringBuilder)
- Don't forget to handle case sensitivity
- Don't ignore character encoding issues

### 🧠 Memory Aids:
- **"Strings are immutable"**
- **"Use equals() not == for comparison"**
- **"StringBuilder for multiple concatenations"**

## 🔍 Debugging Tips

1. **Print string length** - Always check if string is empty
2. **Use debugger** - Step through string operations
3. **Check character encoding** - Be aware of Unicode issues
4. **Test with edge cases** - Empty strings, single characters, special characters

## 📚 Further Reading

- [GeeksforGeeks - Strings](https://www.geeksforgeeks.org/string-data-structure/)
- [LeetCode - String Problems](https://leetcode.com/tag/string/)

---

**🎉 Congratulations!** You've mastered Strings. Practice with the problems above to solidify your understanding!

---

**[← Back to DSA Concepts](../README.md)** | **[Previous Topic →](04 - Queues.md)** 