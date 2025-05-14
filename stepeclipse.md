
---

# How to Run Experiment 1 in Eclipse (Step-by-Step)

### **Experiment 1 Recap:**

Generate a random number up to 100 and print whether it is prime or not.

---

## Step 1: Open Eclipse IDE

* Launch **Eclipse** on your computer.
* Choose your workspace folder (or create a new one) where your projects will be saved.

---

## Step 2: Create a New Java Project

1. Click on **File > New > Java Project**.
2. Enter the project name, e.g., `OOPS_Lab`.
3. Click **Finish**.

---

## Step 3: Create a Package

1. Right-click on the **src** folder inside your new project in the **Package Explorer** panel.
2. Select **New > Package**.
3. Name the package as `udhav_08417711923` (or as per your naming convention).
4. Click **Finish**.

---

## Step 4: Create a New Java Class

1. Right-click on the newly created package (`udhav_08417711923`).
2. Select **New > Class**.
3. Enter the class name: `isprime`.
4. Check the box **public static void main(String\[] args)** to create the main method.
5. Click **Finish**.

---

## Step 5: Copy & Paste the Code

Replace the auto-generated code with the following code (your Experiment 1 code with package):

```java
package udhav_08417711923;

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

## Step 6: Save the File

* Press **Ctrl + S** (or File > Save) to save your class.

---

## Step 7: Run the Program

* Right-click on the file `isprime.java` in the **Package Explorer**.
* Click **Run As > Java Application**.

---

## Step 8: View Output

* The **Console** window in Eclipse will display:

  ```
  The number is: <random_number>
  It is (not) a prime number
  ```

  The output will change every time you run because it picks a random number.

---

## Troubleshooting Tips:

* If you get an error **“Package does not exist”**, check if the package name in the code matches the folder structure.
* Make sure your JDK is properly configured in Eclipse.
* If the console is not visible, go to **Window > Show View > Console**.

---

## Summary of Steps:

| Step | Action                 |
| ---- | ---------------------- |
| 1    | Open Eclipse           |
| 2    | Create Java Project    |
| 3    | Create Package         |
| 4    | Create Java Class      |
| 5    | Paste code & save      |
| 6    | Run program            |
| 7    | View output in console |

---

