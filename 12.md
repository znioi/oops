
---

# 📘 Experiment 12: Analyze a Text File to Count Words, Characters, and Vowels

## 📌 Aim:

To design a Java program that reads a text file and calculates the total number of **words**, **characters**, and **vowels** present in the file.

---

## 📚 Theory:

### ✅ Introduction:

In the world of text processing and natural language analysis, it is often necessary to evaluate basic statistics from a given text. This experiment introduces a simple program that performs basic analysis on a file by reading its content and calculating:

* Total number of **words**
* Total number of **characters**
* Total number of **vowels**

This forms the foundation for more advanced tasks like text mining, keyword analysis, and content summarization.

---

### 🔄 Java I/O (Input/Output):

Java provides robust classes in the `java.io` package to handle file operations:

* **FileReader**: Used to read character files.
* **BufferedReader**: Wraps around FileReader to efficiently read text line by line.

These classes allow you to access the content of a file sequentially in a buffered manner, making it efficient even for large files.

---

### 🧠 Text Analysis Logic:

1. **Character Count**:

   * Each character from the file (including spaces) is counted.
   * `line.length()` gives the total number of characters in that line.

2. **Word Count**:

   * The line is split using a regular expression `\\s+`, which matches one or more whitespaces.
   * This gives an array of words for accurate counting.

3. **Vowel Count**:

   * Each character is converted to lowercase for uniformity.
   * The character is checked against the vowels `a`, `e`, `i`, `o`, `u`.

---

### 🔐 Error Handling:

File operations are prone to errors such as missing files or permission issues. Therefore, the program handles:

* **IOException**: Ensures smooth failure handling if the file cannot be read.

---

### 📈 Applications:

* Word processing applications (e.g., Microsoft Word word counter)
* Language analysis tools
* Pre-processing step in NLP (Natural Language Processing)
* Readability and complexity analysis in documents

---

## 💻 Code:

```java
package ABC;

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class TextAnalyzer {
    public static void main(String[] args) {
        String fileName = "input.txt";  // Ensure this file exists in the project directory
        try {
            analyzeTextFile(fileName);
        } catch (IOException e) {
            System.out.println("Error reading file: " + e.getMessage());
        }
    }

    public static void analyzeTextFile(String fileName) throws IOException {
        int wordCount = 0;
        int charCount = 0;
        int vowelCount = 0;

        try (BufferedReader reader = new BufferedReader(new FileReader(fileName))) {
            String line;
            while ((line = reader.readLine()) != null) {
                charCount += line.length();

                String[] words = line.trim().split("\\s+");
                if (!line.trim().isEmpty()) {
                    wordCount += words.length;
                }

                for (char c : line.toLowerCase().toCharArray()) {
                    if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
                        vowelCount++;
                    }
                }
            }
        }

        System.out.println("Analysis of " + fileName + ":");
        System.out.println("Number of words: " + wordCount);
        System.out.println("Number of characters: " + charCount);
        System.out.println("Number of vowels: " + vowelCount);
    }
}
```

---

## 📄 Sample Input File (`input.txt`):

```
Java is a powerful programming language.
It is widely used in enterprise and mobile applications.
```

## 📤 Sample Output:

```
Analysis of input.txt:
Number of words: 14
Number of characters: 93
Number of vowels: 37
```

---

## ✅ Conclusion:

This experiment demonstrates basic file handling and string processing capabilities in Java. By using Java's I/O classes and fundamental string operations, we can effectively perform text analysis that serves as a stepping stone for more complex data processing tasks.

---

