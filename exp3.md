
---

# Experiment 3 - Array Operations: Sum and Average

## 📌 Aim:

To find the **sum** and **average** of an array of N numbers entered by the user using Java.

---

## 📚 Theory:

An array is a data structure used to store multiple values of the same type. To calculate the **sum** and **average** of elements:

* **Sum**: Add all the elements using a loop.
* **Average**: Divide the sum by the number of elements (N).

This program takes `N` as input from the user, reads `N` integers, calculates the sum of all elements, and then computes the average.

---

## 💻 Code:

```java
package ABC;

import java.util.Scanner;

public class arraysum {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Enter the number of elements in the array: ");
        int n = sc.nextInt();
        int[] numbers = new int[n];
        System.out.println("Enter the numbers:");
        for (int i = 0; i < n; i++) {
            numbers[i] = sc.nextInt();
        }
        
        int sum = 0;
        for (int number : numbers) {
            sum += number; 
        }
        double average = (double) sum / n;

        System.out.println("Sum: " + sum);
        System.out.println("Average: " + average);
    }
}
```

---

## 🧾 Sample Output:

```
Enter the number of elements in the array: 5
Enter the numbers:
10
20
30
40
50
Sum: 150
Average: 30.0
```

---

Let me know if you'd like this as a `.md` file or want the next experiment’s documentation too.
