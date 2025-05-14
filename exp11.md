
---

# 📘 Experiment 11: File Handling — Reading from and Writing to Text Files

## 📌 Aim:

Design a program to read the contents of a text file, display it on the screen, and then write the same content into another text file.

---

## 📚 Theory:

### File Handling in Java:

File handling is a crucial part of Java programming which allows you to create, read, write, and manipulate files stored on the disk. Java provides several classes for file handling, primarily in the `java.io` package.

### Key Classes Used:

* **`FileReader`**: Reads data from a file character by character.
* **`BufferedReader`**: Buffers the input for efficient reading of text.
* **`FileWriter`**: Writes character streams to files.
* **`BufferedWriter`**: Buffers the output for efficient writing.

### Process Overview:

1. Open the source file using `FileReader` wrapped in a `BufferedReader`.
2. Read the file content line-by-line and print it to the console.
3. Write the same lines to a destination file using `FileWriter` and `BufferedWriter`.
4. Properly handle exceptions and close all resources to avoid memory leaks.

---

## 💻 Code:

```java
package ABC;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;

public class FileCopy {
    public static void main(String[] args) {
        String sourceFile = "input.txt";    // Source file to read from
        String destinationFile = "output.txt"; // Destination file to write to

        try (
            BufferedReader reader = new BufferedReader(new FileReader(sourceFile));
            BufferedWriter writer = new BufferedWriter(new FileWriter(destinationFile));
        ) {
            String line;
            System.out.println("Contents of " + sourceFile + ":");
            while ((line = reader.readLine()) != null) {
                System.out.println(line);       // Print line to console
                writer.write(line);              // Write line to destination file
                writer.newLine();                // Add newline in output file
            }
            System.out.println("\nContent successfully copied to " + destinationFile);
        } catch (IOException e) {
            System.out.println("An error occurred: " + e.getMessage());
        }
    }
}
```

---

## 📄 Sample Output:

Assuming `input.txt` contains:

```
Hello, this is line one.
This is line two.
This is the last line.
```

Output on console:

```
Contents of input.txt:
Hello, this is line one.
This is line two.
This is the last line.

Content successfully copied to output.txt
```

The file `output.txt` will have the same content as `input.txt`.

---

## ✅ Conclusion:

This program successfully demonstrates file reading and writing operations in Java. It reads text from an existing file, displays the content on the console, and writes the same content to a new file, showcasing efficient handling of files using `BufferedReader` and `BufferedWriter`.

---

