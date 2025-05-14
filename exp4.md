
---

# Experiment 4 - Constructor Overloading in a Rectangle Class

## 📌 Aim:

To implement a Java program that demonstrates **constructor overloading** using a `Rectangle` class and performs basic area and perimeter calculations.

---

## 📚 Theory:

**Constructor Overloading** is a feature in Java where a class can have more than one constructor with different parameter lists. This allows objects to be initialized in different ways:

* **Default constructor**: Initializes attributes to default values.
* **Parameterized constructor**: Initializes attributes with provided values.
* **Copy constructor**: Creates a new object by copying another object.

This program:

* Accepts `length` and `breadth` from the user.
* Demonstrates all three constructor types.
* Computes and displays the area and perimeter for each `Rectangle` object.

---

## 💻 Code:

```java
package ABC;

import java.util.Scanner;

class Rectangle {
    private double length, breadth;

    public Rectangle() {
        this(0, 0);  
    }

    public Rectangle(double length, double breadth) {
        this.length = length;
        this.breadth = breadth;
    }

    public Rectangle(Rectangle rect) {
        this(rect.length, rect.breadth);
    }

    public double getLength() { return length; }
    public double getBreadth() { return breadth; }

    public void setDimensions(double length, double breadth) {
        this.length = length;
        this.breadth = breadth;
    }

    public double getArea() { return length * breadth; }
    public double getPerimeter() { return 2 * (length + breadth); }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter length: ");
        double length = sc.nextDouble();
        System.out.print("Enter breadth: ");
        double breadth = sc.nextDouble();

        Rectangle rect1 = new Rectangle();
        rect1.setDimensions(length, breadth);
        displayRectangleDetails("Default constructor", rect1);

        Rectangle rect2 = new Rectangle(length, breadth);
        displayRectangleDetails("Parameterized constructor", rect2);

        Rectangle rect3 = new Rectangle(rect2);
        displayRectangleDetails("Copy constructor", rect3);

        sc.close();
    }

    private static void displayRectangleDetails(String constructorType, Rectangle rect) {
        System.out.println(constructorType + ":");
        System.out.println("Length: " + rect.getLength() + ", Breadth: " + rect.getBreadth());
        System.out.println("Area: " + rect.getArea() + ", Perimeter: " + rect.getPerimeter());
        System.out.println();
    }
}
```

---

## 🧾 Sample Output:

```
Enter length: 5
Enter breadth: 4
Default constructor:
Length: 5.0, Breadth: 4.0
Area: 20.0, Perimeter: 18.0

Parameterized constructor:
Length: 5.0, Breadth: 4.0
Area: 20.0, Perimeter: 18.0

Copy constructor:
Length: 5.0, Breadth: 4.0
Area: 20.0, Perimeter: 18.0
```

---

