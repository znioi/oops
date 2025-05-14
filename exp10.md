
---

# 📘 Experiment 10: Basic Calculator using AWT and Event Handling

## 📌 Aim:

To design and implement a **Basic Calculator** using **AWT components** and **Event Handling** mechanisms in Java.

---

## 📚 Theory:

### ✅ Introduction:

In Java GUI programming, **AWT (Abstract Window Toolkit)** provides the foundation for building graphical user interfaces. For real-time interaction, **event handling** is used to respond to user inputs such as button clicks or key presses. This experiment demonstrates how to use these tools to build a **calculator application** capable of evaluating arithmetic expressions.

### 🧩 AWT Components Used:

* **Frame**: The main window of the calculator.
* **Panel**: To organize buttons in a grid layout.
* **Button**: For digits and arithmetic operators (+, -, \*, /, =).
* **TextArea**: To display the input expression and result.

### 🔁 Event Handling:

Java uses **event-driven programming**. When a user clicks a button, an **event** is generated. This is handled using:

* **ActionListener interface** – for responding to button clicks.
* **WindowAdapter** – to handle window closing events.

### 🧠 Expression Evaluation:

Arithmetic expressions entered by the user (e.g., `3 + 5 * 2`) are parsed and evaluated in two steps:

1. **Infix to Postfix Conversion**: Infix notation is user-friendly but harder to evaluate programmatically. It is converted to postfix (Reverse Polish Notation) for easier evaluation using a **stack**.
2. **Postfix Evaluation**: The postfix expression is evaluated using another stack, applying operators on the last two operands encountered.

### 🔐 Advantages of This Design:

* Modular design separates logic (expression evaluation) from UI (buttons, layout).
* Ensures **reusability** and **readability**.
* Handles **invalid input** gracefully with exception handling.
* Demonstrates **event-driven GUI programming**, an important real-world Java concept.

---

## 💻 Code:

```java
package ABC;

import java.awt.*;
import java.awt.event.*;
import java.util.Stack;

class Comp {

    private boolean isOperand(char c) {
        return Character.isDigit(c);
    }

    private boolean isOperator(char c) {
        return c == '+' || c == '-' || c == '*' || c == '/';
    }

    private int precedence(char op) {
        switch (op) {
            case '+': case '-': return 1;
            case '*': case '/': return 2;
        }
        return 0;
    }

    public String infixToPostfix(String expr) {
        StringBuilder result = new StringBuilder();
        Stack<Character> stack = new Stack<>();

        for (int i = 0; i < expr.length(); i++) {
            char c = expr.charAt(i);
            if (Character.isWhitespace(c)) continue;

            if (isOperand(c)) {
                result.append(c);
            } else if (c == '(') {
                stack.push(c);
            } else if (c == ')') {
                while (!stack.isEmpty() && stack.peek() != '(') {
                    result.append(stack.pop());
                }
                if (!stack.isEmpty() && stack.peek() == '(') {
                    stack.pop();
                }
            } else if (isOperator(c)) {
                while (!stack.isEmpty() && precedence(stack.peek()) >= precedence(c)) {
                    result.append(stack.pop());
                }
                stack.push(c);
            }
        }

        while (!stack.isEmpty()) {
            result.append(stack.pop());
        }

        return result.toString();
    }

    public int evaluatePostfix(String postfix) {
        Stack<Integer> stack = new Stack<>();

        for (int i = 0; i < postfix.length(); i++) {
            char c = postfix.charAt(i);

            if (Character.isDigit(c)) {
                stack.push(c - '0');
            } else if (isOperator(c)) {
                int b = stack.pop();
                int a = stack.pop();
                switch (c) {
                    case '+': stack.push(a + b); break;
                    case '-': stack.push(a - b); break;
                    case '*': stack.push(a * b); break;
                    case '/': stack.push(a / b); break;
                }
            }
        }

        return stack.pop();
    }

    public String evaluate(String input) {
        try {
            String postfix = infixToPostfix(input);
            int result = evaluatePostfix(postfix);
            return String.valueOf(result);
        } catch (Exception e) {
            return "Error";
        }
    }
}

public class Calc extends Frame {
    TextArea tf;

    class MyFrame extends Panel {
        Button createButton(String label, TextArea tf) {
            Button b = new Button(label);
            b.addActionListener(e -> tf.setText(tf.getText() + " " + label));
            return b;
        }

        MyFrame() {
            Comp comp = new Comp();
            Button bequal = new Button("=");
            bequal.addActionListener(e -> {
                String input = tf.getText();
                String output = comp.evaluate(input);
                tf.setText(output);
            });

            setSize(400, 400);
            setBackground(Color.BLUE);
            add(createButton("0", tf));
            add(createButton("1", tf));
            add(createButton("2", tf));
            add(createButton("3", tf));
            add(createButton("4", tf));
            add(createButton("5", tf));
            add(createButton("6", tf));
            add(createButton("7", tf));
            add(createButton("8", tf));
            add(createButton("9", tf));
            add(createButton("+", tf));
            add(createButton("-", tf));
            add(createButton("/", tf));
            add(createButton("*", tf));
            add(bequal);
            setLayout(new GridLayout(3, 5));
            setVisible(true);
        }
    }

    Calc() {
        setTitle("Calculator by Udhav");
        setSize(500, 500);
        setBackground(Color.RED);
        setLayout(new BorderLayout());
        tf = new TextArea();
        tf.setFont(new Font("Arial", Font.BOLD, 18));
        add(tf, BorderLayout.NORTH);
        add(new MyFrame());
        setVisible(true);
    }

    public static void main(String[] args) {
        Calc c = new Calc();
        c.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}
```

---

## 🧾 Sample Output:

```
When you click:
[2] [+] [3] [=]
Output shown in TextArea:
5

If invalid expression entered:
Output: Error
```

---

