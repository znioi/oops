
---

# Experiment 2 - Fibonacci Series and Factorial using Recursion

## 📌 Aim:

A. To generate the first 10 terms of the Fibonacci series.
B. To find the factorial of a given number using recursion.

---

## 📚 Theory:

### A. Fibonacci Series:

The Fibonacci sequence is a series where each term is the sum of the two preceding ones, starting from 0 and 1:

```
0, 1, 1, 2, 3, 5, 8, 13, ...
```

It is widely used in mathematics and computer science for its recursive nature and pattern generation.

### B. Factorial using Recursion:

The **factorial** of a number `n` (denoted as `n!`) is the product of all positive integers less than or equal to `n`.
Using recursion:

* Base case: `fact(0) = 1`
* Recursive case: `fact(n) = n * fact(n - 1)`

---

## 💻 Code:

### 🔹 exp2a - Fibonacci Series

```java
// exp2a - package uv_17711923;
package uv_17711923;

public class FibonacciSequence {
    public static void main(String[] args) {
        int N = 10;
        Fibonacci(N);
    }

    public static void Fibonacci(int N) {
        int num1 = 0;
        int num2 = 1;
        for (int i = 0; i < N; i++) {
            System.out.println(num1 + " ");
            int num3 = num2 + num1;
            num1 = num2;
            num2 = num3;
        }
    }
}
```

### 🔹 exp2b - Factorial using Recursion

```java
// exp2b - package uv_17711923;
package uv_17711923;

public class fact {
    public static void main(String[] args) {
        int num = 5;
        System.out.println("The factorial of the number is:");
        System.out.println(fact(num));
    }

    static int fact(int num) {
        if (num == 0 || num == 1) {
            return 1;
        }
        return fact(num - 1) * num;
    }
}
```

---

## 🧾 Sample Output:

### ▶ Output for Fibonacci Series:

```
0 
1 
1 
2 
3 
5 
8 
13 
21 
34 
```

### ▶ Output for Factorial:

```
The factorial of the number is:
120
```

---

