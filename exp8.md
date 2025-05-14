
---

# 📘 Experiment 8: Multithreading using Thread Class

## 📌 Aim:

To design a program that demonstrates multithreading in Java by extending the `Thread` class.

---

## 📚 Theory:

### What is Multithreading?

Multithreading is a Java feature that allows concurrent execution of two or more threads to maximize CPU utilization. A thread is a lightweight subprocess, the smallest unit of processing, within a program.

### Benefits of Multithreading:

* Improves performance by performing multiple tasks simultaneously.
* Helps in resource sharing between threads.
* Enhances the responsiveness of applications.

### Ways to Create Threads:

1. **By extending the Thread class**: Override the `run()` method and create instances of the subclass.
2. **By implementing Runnable interface**: Implement `run()` method and pass an instance to a Thread object.

In this experiment, we demonstrate the first method — extending the `Thread` class.

### Important Methods in Thread Class:

* `start()`: Starts the thread and calls the `run()` method internally.
* `run()`: Contains the code executed by the thread.
* `sleep(ms)`: Pauses the thread for specified milliseconds.
* `getName()`: Returns the thread name.
* `setName()`: Sets the thread name.

---

## 💻 Code:

```java
package ABC;

class MyThread extends Thread {
    private String threadName;

    MyThread(String name) {
        this.threadName = name;
        setName(threadName);
    }

    @Override
    public void run() {
        for (int i = 1; i <= 5; i++) {
            System.out.println(getName() + " is running: Count " + i);
            try {
                Thread.sleep(500); // Sleep for 500 milliseconds
            } catch (InterruptedException e) {
                System.out.println(getName() + " interrupted.");
            }
        }
        System.out.println(getName() + " has finished execution.");
    }
}

public class MultiThreadDemo {
    public static void main(String[] args) {
        MyThread t1 = new MyThread("Thread-A");
        MyThread t2 = new MyThread("Thread-B");

        t1.start(); // Start first thread
        t2.start(); // Start second thread

        System.out.println("Main thread is running.");
    }
}
```

---

## 📄 Sample Output:

```
Main thread is running.
Thread-A is running: Count 1
Thread-B is running: Count 1
Thread-A is running: Count 2
Thread-B is running: Count 2
Thread-A is running: Count 3
Thread-B is running: Count 3
Thread-A is running: Count 4
Thread-B is running: Count 4
Thread-A is running: Count 5
Thread-B is running: Count 5
Thread-A has finished execution.
Thread-B has finished execution.
```

---

## ✅ Conclusion:

This experiment illustrates how multiple threads can run concurrently by extending the `Thread` class. Each thread executes its own `run()` method, and thread scheduling is managed by the JVM, allowing simultaneous execution and improving efficiency.

---

