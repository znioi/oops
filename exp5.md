
---

# 📘 Experiment 5: String Operations in Java

## 📌 Aim:

Design a Java program to perform basic string operations such as:

* Checking if two strings are equal
* Reversing a string
* Changing the case of a string (uppercase to lowercase and vice versa)

---

## 📚 Theory:

### 🔤 Strings in Java:

Strings in Java are objects that represent sequences of characters. They are widely used for storing and manipulating text data.

### 🔄 String Operations:

1. **Equality Check**:

   * The `equals()` method compares the content of two strings.
   * It returns `true` if the strings contain the exact same sequence of characters.

2. **Reversing a String**:

   * Reversing means writing the characters of the string in reverse order.
   * Can be done by iterating from the end of the string to the start or by using built-in classes like `StringBuilder`.

3. **Changing Case**:

   * Strings can be converted to all uppercase letters using `toUpperCase()`.
   * Similarly, `toLowerCase()` converts all letters to lowercase.
   * Changing case can be useful for formatting and case-insensitive comparisons.

---

### ⚙️ Application:

String manipulation is fundamental in software development—used in user input handling, data validation, formatting outputs, parsing, etc.

---

## 💻 Code:

```java
package ABC;

import java.util.Scanner;

public class StringOperations {

    // Method to check equality of two strings
    public static boolean isEqual(String str1, String str2) {
        return str1.equals(str2);
    }

    // Method to reverse a string
    public static String reverseString(String str) {
        StringBuilder reversed = new StringBuilder(str);
        return reversed.reverse().toString();
    }

    // Method to change case: uppercase to lowercase and vice versa
    public static String changeCase(String str) {
        StringBuilder changed = new StringBuilder();

        for (char ch : str.toCharArray()) {
            if (Character.isUpperCase(ch)) {
                changed.append(Character.toLowerCase(ch));
            } else if (Character.isLowerCase(ch)) {
                changed.append(Character.toUpperCase(ch));
            } else {
                changed.append(ch);  // Non-alphabetical characters remain unchanged
            }
        }

        return changed.toString();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter first string: ");
        String s1 = scanner.nextLine();

        System.out.print("Enter second string: ");
        String s2 = scanner.nextLine();

        System.out.println("\nString Equality: " + isEqual(s1, s2));

        System.out.println("Reverse of first string: " + reverseString(s1));

        System.out.println("Change case of first string: " + changeCase(s1));

        scanner.close();
    }
}
```

---

## 📄 Sample Input:

```
Enter first string: HelloWorld
Enter second string: helloworld
```

## 📤 Sample Output:

```
String Equality: false
Reverse of first string: dlroWolleH
Change case of first string: hELLOwORLD
```

---

## ✅ Conclusion:

This experiment helps in understanding fundamental string manipulation methods in Java such as equality checking, reversing, and changing case, which are commonly used in various programming scenarios involving text data.

---

