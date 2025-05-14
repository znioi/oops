You're right — I forgot to **change** the package name in the code comment. Here's the corrected and final version of the `README` for **exp1.md**, with **consistent package naming**:

---

# Experiment 1 - Prime Number Check using Random Number Generation

## 📌 Aim:

To generate a random number up to 100 and print whether it is a prime number using Java.

---

## 📚 Theory:

A **prime number** is a number greater than 1 that has no positive divisors other than 1 and itself. To check for primality:

* Numbers less than 2 are **not prime**.
* A number is **not prime** if it is divisible by any number from 2 to half of the number.
* Otherwise, it is **prime**.

In this experiment, Java's `Random` class is used to generate a random number from 1 to 100. Then, a function checks if this number is prime and prints the result accordingly.

---

## 💻 Code:

```java
// exp1 - package uv_17711923;
package uv_17711923;

import java.util.Random;

public class isprime {
    public static void main(String[] args) {
        Random ran = new Random();
        int num = ran.nextInt(100) + 1;
        System.out.println("The number is: " + num);
        checkprime(num);
    }

    public static void checkprime(int num) {
        if (num < 2) {
            System.out.println("It is not a prime number");
            return;
        }
        for (int i = 2; i <= num / 2; i++) {
            if (num % i == 0) {
                System.out.println("It is not a prime number");
                return;
            }
        }
        System.out.println("It is a prime number");
    }
}
```

---

## 🧾 Sample Output:

```
The number is: 73
It is a prime number
```

> *Note: The output will vary each time you run the program since the number is randomly generated.*

---

