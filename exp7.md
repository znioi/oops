
---

# 📘 Experiment 7: Exception Handling in Java

## 📌 Aim:

To demonstrate the use of **try**, **catch**, **finally**, **throw**, and **throws** in Java for effective exception handling.

---

## 📚 Theory:

### Exception Handling in Java:

Exception handling is a powerful mechanism to handle runtime errors, allowing a program to continue execution or terminate gracefully.

* **try block:** Contains code that might throw an exception.
* **catch block:** Handles the exception thrown by the try block.
* **finally block:** Always executes after try and catch blocks, used for cleanup activities.
* **throw:** Used to explicitly throw an exception.
* **throws:** Declares exceptions that a method might throw, allowing the caller to handle them.

### Keywords:

* **try**: Wraps code that may cause exceptions.
* **catch(ExceptionType e)**: Catches and handles the exception of specified type.
* **finally**: Executes regardless of exception occurrence, ideal for closing resources.
* **throw**: Used to throw an exception manually.
* **throws**: Declares checked exceptions in method signature for caller awareness.

---

## 💻 Code:

```java
package ABC;

import java.util.Scanner;

// Custom Exception class for demonstration
class NegativeNumberException extends Exception {
    public NegativeNumberException(String message) {
        super(message);
    }
}

public class ExceptionHandlingDemo {

    // Method demonstrating 'throws' and 'throw'
    public static int divide(int a, int b) throws ArithmeticException {
        if (b == 0) {
            throw new ArithmeticException("Cannot divide by zero!");
        }
        return a / b;
    }

    // Method that throws a custom checked exception
    public static void checkPositive(int num) throws NegativeNumberException {
        if (num < 0) {
            throw new NegativeNumberException("Negative number entered: " + num);
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        try {
            System.out.print("Enter numerator: ");
            int num = scanner.nextInt();

            System.out.print("Enter denominator: ");
            int denom = scanner.nextInt();

            // Throws ArithmeticException if denom is zero
            int result = divide(num, denom);
            System.out.println("Result: " + result);

            System.out.print("Enter a positive number: ");
            int number = scanner.nextInt();

            // Throws custom NegativeNumberException if number is negative
            checkPositive(number);
            System.out.println(number + " is positive.");

        } catch (ArithmeticException e) {
            System.out.println("ArithmeticException caught: " + e.getMessage());
        } catch (NegativeNumberException e) {
            System.out.println("NegativeNumberException caught: " + e.getMessage());
        } catch (Exception e) {
            System.out.println("Some other exception caught: " + e.getMessage());
        } finally {
            System.out.println("Finally block executed. Closing resources.");
            scanner.close();
        }
    }
}
```

---

## 📄 Sample Input/Output:

```
Enter numerator: 10
Enter denominator: 0
ArithmeticException caught: Cannot divide by zero!
Finally block executed. Closing resources.
```

---

```
Enter numerator: 10
Enter denominator: 2
Result: 5
Enter a positive number: -7
NegativeNumberException caught: Negative number entered: -7
Finally block executed. Closing resources.
```

---

## ✅ Conclusion:

This program clearly demonstrates the usage of:

* **try**: to wrap code that can cause exceptions.
* **catch**: to handle specific exceptions (`ArithmeticException`, `NegativeNumberException`).
* **finally**: to perform cleanup, executing regardless of exceptions.
* **throw**: to manually throw exceptions when specific conditions occur.
* **throws**: to declare exceptions that might be thrown by methods, allowing calling code to handle them.

Effective exception handling ensures robust and error-resilient Java applications.

---

