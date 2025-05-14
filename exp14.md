
---

# 📘 Experiment 14: Connect to a Database and Display Contents of a Table

## 📌 Aim:

To design a Java program that connects to a database, retrieves, and displays the contents of a specified table.

---

## 📚 Theory:

### What is Database Connectivity?

Database connectivity enables a program to interact with a database system to perform operations like reading, writing, updating, and deleting data. In Java, this is typically done using **JDBC** (Java Database Connectivity) API.

### Java Database Connectivity (JDBC):

JDBC is a standard Java API for connecting and executing queries with databases. It provides a set of interfaces and classes to work with databases regardless of the underlying database vendor.

### Main Components of JDBC:

* **DriverManager**: Manages a list of database drivers. Establishes connections with the appropriate driver based on the database URL.
* **Connection**: Represents a session with a specific database.
* **Statement**: Used to execute static SQL queries.
* **ResultSet**: Holds data retrieved from executing queries.
* **SQLException**: Handles database errors.

### Steps to Connect and Retrieve Data:

1. **Load the database driver** (optional in newer JDBC versions).
2. **Establish connection** using `DriverManager.getConnection()` with database URL, username, and password.
3. **Create a Statement** object from the connection.
4. **Execute SQL query** using the Statement.
5. **Process the ResultSet** returned by the query.
6. **Close all resources** (ResultSet, Statement, Connection).

### Why Is This Important?

Connecting Java applications to databases allows persistent data storage and retrieval, essential for real-world applications like inventory management, banking, e-commerce, and more.

### Prerequisites:

* Have a database installed (e.g., MySQL, PostgreSQL).
* A table with some data to query.
* The JDBC driver jar for your database added to the project classpath.

---

## 💻 Code Example (Using MySQL):

```java
package ABC;

import java.sql.*;

public class DatabaseDisplay {
    public static void main(String[] args) {
        // Database URL and credentials
        String url = "jdbc:mysql://localhost:3306/mydatabase"; // replace 'mydatabase' with your DB name
        String user = "root";  // your DB username
        String password = "password"; // your DB password

        // Query to fetch all records from the table 'employees'
        String query = "SELECT * FROM employees";

        try (
            // Step 2: Establish connection
            Connection con = DriverManager.getConnection(url, user, password);
            // Step 3: Create statement
            Statement stmt = con.createStatement();
            // Step 4: Execute query and get results
            ResultSet rs = stmt.executeQuery(query);
        ) {
            System.out.println("ID\tName\t\tDepartment\tSalary");
            System.out.println("-----------------------------------------------");

            // Step 5: Process ResultSet
            while (rs.next()) {
                int id = rs.getInt("id");
                String name = rs.getString("name");
                String dept = rs.getString("department");
                double salary = rs.getDouble("salary");

                System.out.printf("%d\t%s\t\t%s\t\t%.2f%n", id, name, dept, salary);
            }
        } catch (SQLException e) {
            System.out.println("Database error: " + e.getMessage());
        }
    }
}
```

---

## 📄 Sample Output:

```
ID      Name            Department      Salary
-----------------------------------------------
101     John Doe        IT              75000.00
102     Jane Smith      HR              68000.00
103     Mike Johnson    Finance         72000.00
```

---

## ✅ Conclusion:

This experiment demonstrates the basic procedure to connect a Java program to a relational database, execute SQL queries, and process results using JDBC. It forms the foundation for building Java applications with database integration, essential for data-driven software solutions.

---

