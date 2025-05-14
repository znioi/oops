
---

# 📘 Experiment 13: Simple Chat Application Using Socket Programming

## 📌 Aim:

To design a simple client-server chat application in Java using socket programming that allows two-way communication between a client and a server.

---

## 📚 Theory:

### What is Socket Programming?

Socket programming is a way to enable communication between two computers over a network. It uses endpoints called **sockets** to send and receive data. A socket is defined by an IP address and a port number.

### Key Concepts:

* **Server Socket**: Listens for incoming client connection requests on a specified port.
* **Client Socket**: Initiates a connection to the server socket.
* **Input and Output Streams**: Used to send and receive data between client and server.

### How Does It Work?

1. The **server** creates a `ServerSocket` and waits for a connection request.
2. The **client** creates a `Socket` to connect to the server’s IP and port.
3. Once connected, both client and server establish input and output streams to exchange messages.
4. Communication continues in a loop until either party terminates the connection.

### Importance in Real Life:

Socket programming underpins many networked applications such as chat apps, web servers, multiplayer games, and real-time communication tools.

---

## 💻 Code:

We implement two separate programs:

### 1. Server Side (`ChatServer.java`):

```java
package ABC;

import java.io.*;
import java.net.*;

public class ChatServer {
    public static void main(String[] args) {
        try (ServerSocket serverSocket = new ServerSocket(5000)) {
            System.out.println("Server started. Waiting for client...");
            Socket clientSocket = serverSocket.accept();
            System.out.println("Client connected.");

            BufferedReader in = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()));
            BufferedWriter out = new BufferedWriter(new OutputStreamWriter(clientSocket.getOutputStream()));
            BufferedReader consoleReader = new BufferedReader(new InputStreamReader(System.in));

            String clientMessage, serverMessage;
            System.out.println("Start chatting (type 'exit' to quit):");

            while (true) {
                // Read message from client
                clientMessage = in.readLine();
                if (clientMessage == null || clientMessage.equalsIgnoreCase("exit")) {
                    System.out.println("Client disconnected.");
                    break;
                }
                System.out.println("Client: " + clientMessage);

                // Read message from server console
                System.out.print("Server: ");
                serverMessage = consoleReader.readLine();
                out.write(serverMessage);
                out.newLine();
                out.flush();

                if (serverMessage.equalsIgnoreCase("exit")) {
                    System.out.println("Server terminated the chat.");
                    break;
                }
            }

            clientSocket.close();
            System.out.println("Connection closed.");
        } catch (IOException e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

---

### 2. Client Side (`ChatClient.java`):

```java
package ABC;

import java.io.*;
import java.net.*;

public class ChatClient {
    public static void main(String[] args) {
        String serverAddress = "localhost"; // or IP address of server
        int port = 5000;

        try (Socket socket = new Socket(serverAddress, port)) {
            System.out.println("Connected to the server.");

            BufferedReader in = new BufferedReader(new InputStreamReader(socket.getInputStream()));
            BufferedWriter out = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream()));
            BufferedReader consoleReader = new BufferedReader(new InputStreamReader(System.in));

            String clientMessage, serverMessage;
            System.out.println("Start chatting (type 'exit' to quit):");

            while (true) {
                // Read message from server
                serverMessage = in.readLine();
                if (serverMessage == null || serverMessage.equalsIgnoreCase("exit")) {
                    System.out.println("Server disconnected.");
                    break;
                }
                System.out.println("Server: " + serverMessage);

                // Read message from client console
                System.out.print("Client: ");
                clientMessage = consoleReader.readLine();
                out.write(clientMessage);
                out.newLine();
                out.flush();

                if (clientMessage.equalsIgnoreCase("exit")) {
                    System.out.println("Client terminated the chat.");
                    break;
                }
            }

            socket.close();
            System.out.println("Connection closed.");
        } catch (IOException e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

---

## 📄 Sample Run:

**Server Console:**

```
Server started. Waiting for client...
Client connected.
Start chatting (type 'exit' to quit):
Client: Hello Server!
Server: Hello Client!
Client: How are you?
Server: I'm good, thanks.
Client: exit
Client disconnected.
Connection closed.
```

**Client Console:**

```
Connected to the server.
Start chatting (type 'exit' to quit):
Server: Hello Client!
Client: Hello Server!
Server: I'm good, thanks.
Client: How are you?
Client: exit
Client terminated the chat.
Connection closed.
```

---

## ✅ Conclusion:

This experiment demonstrates the fundamentals of socket programming to create a simple chat application enabling real-time communication between a client and server. It highlights network programming concepts such as sockets, streams, and client-server architecture, which are essential in building networked applications.

---

