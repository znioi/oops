
---

# Experiment 6 - Demonstrating the `final` Keyword in Java

## 📌 Aim:

To demonstrate the use of the `final` keyword in Java with final **classes**, **data members**, and **methods**.

---

## 📚 Theory:

The `final` keyword in Java is used to restrict the user:

* **Final variable**: Value cannot be changed once assigned.
* **Final method**: Cannot be overridden in subclasses.
* **Final class**: Cannot be inherited or extended.

### Use Cases:

* Ensure constants (like `MAX_SPEED`) are not accidentally changed.
* Protect core functionality from being modified via inheritance.

---

## 💻 Code:

```java
package ABC;

public class exp6 {
    // Final Class Example
    static final class FinalClass {
        // Final Data Member
        final int MAX_SPEED = 120;

        // Final Method
        public final void displayMaxSpeed() {
            System.out.println("The maximum speed is: " + MAX_SPEED);
        }
    }

    // Main class to demonstrate the final keyword
    public static class FinalKeywordDemo {
        public static void main(String[] args) {
            // Creating an object of FinalClass
            FinalClass car = new FinalClass();
            car.displayMaxSpeed(); // Calling the final method

            // Demonstrating Final Data Member
            System.out.println("MAX_SPEED: " + car.MAX_SPEED);

            // Uncommenting the below line will cause a compilation error in Eclipse
            // car.MAX_SPEED = 150;  // Cannot modify a final variable

            // Demonstrating that a final method cannot be overridden:
            // The following subclass declaration will result in a compilation error.
            // Uncomment the below block to see the error in Eclipse.
            
            /*
            class SubClass extends FinalClass {
                @Override
                public void displayMaxSpeed() {
                    System.out.println("Trying to override a final method.");
                }
            }
            */
        }
    }
}
```

---

## 🧾 Sample Output:

```
The maximum speed is: 120
MAX_SPEED: 120
```

> 💡 **Note**:
>
> * Attempting to change a final variable or override a final method will result in a **compile-time error**.
> * The commented code block can be tried in an IDE like Eclipse to observe these errors.

---

