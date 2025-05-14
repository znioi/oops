
---

# Experiment 9 - Tic Tac Toe Game in Java

## 📌 Aim:

To design and implement a console-based **Tic Tac Toe** game using Java for two players.

---

## 📚 Theory:

**Tic Tac Toe** is a two-player strategy game played on a 3×3 grid. Players alternate turns, placing their symbol (either 'X' or 'O') in empty cells. The objective is to place three of their symbols in a row — horizontally, vertically, or diagonally — before the opponent does. If all the cells are filled and neither player has achieved this, the game ends in a **draw**.

### Key Concepts Demonstrated in This Program:

1. **Arrays**: A 2D `char` array is used to represent the 3x3 game board.
2. **Control Flow**: Conditional statements (`if`, `else if`) and loops (`while`, `for`) drive the game logic and ensure correct turns, moves, and win checks.
3. **Switching Turns**: The current player switches between 'X' and 'O' after every valid move.
4. **User Input**: The program uses `Scanner` to accept player input and update the board accordingly.
5. **Winner Detection**: After every move, the game checks:

   * All rows for equal symbols.
   * All columns for equal symbols.
   * Both diagonals for equal symbols.
6. **Game End Conditions**:

   * If a player aligns three of their marks, they win.
   * If the board is full (9 moves) with no winner, the game is a draw.
7. **Input Validation**: If the player selects an already occupied cell or enters an invalid number, the program alerts the user and retries.

This implementation helps students understand how **game logic**, **input validation**, and **state management** work together in an interactive application. It also emphasizes modular code design through the use of well-named methods like `makeMove()`, `checkWinner()`, and `printBoard()`.

---

## 💻 Code:

```java
package ABC;

import java.util.Scanner;

public class TicTacToe {
    private static char[][] board = {
        {'1', '2', '3'},
        {'4', '5', '6'},
        {'7', '8', '9'}
    };
    private static char currentPlayer = 'X';

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int moves = 0;

        while (true) {
            printBoard();
            System.out.print("Player " + currentPlayer + ", enter a number (1-9): ");
            int move = scanner.nextInt();

            if (!makeMove(move)) {
                System.out.println("Invalid move! Try again.");
                continue;
            }

            moves++;
            if (checkWinner()) {
                printBoard();
                System.out.println("Player " + currentPlayer + " wins!");
                break;
            } else if (moves == 9) {
                printBoard();
                System.out.println("It's a draw!");
                break;
            }

            currentPlayer = (currentPlayer == 'X') ? 'O' : 'X';
        }

        scanner.close();
    }

    private static void printBoard() {
        System.out.println("\n " + board[0][0] + " | " + board[0][1] + " | " + board[0][2]);
        System.out.println("---+---+---");
        System.out.println(" " + board[1][0] + " | " + board[1][1] + " | " + board[1][2]);
        System.out.println("---+---+---");
        System.out.println(" " + board[2][0] + " | " + board[2][1] + " | " + board[2][2] + "\n");
    }

    private static boolean makeMove(int move) {
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                if (board[i][j] == (char) (move + '0')) {
                    board[i][j] = currentPlayer;
                    return true;
                }
            }
        }
        return false;
    }

    private static boolean checkWinner() {
        for (int i = 0; i < 3; i++) {
            if (board[i][0] == board[i][1] && board[i][1] == board[i][2]) return true;
            if (board[0][i] == board[1][i] && board[1][i] == board[2][i]) return true;
        }
        return (board[0][0] == board[1][1] && board[1][1] == board[2][2]) ||
               (board[0][2] == board[1][1] && board[1][1] == board[2][0]);
    }
}
```

---

## 🧾 Sample Output:

```
 1 | 2 | 3
---+---+---
 4 | 5 | 6
---+---+---
 7 | 8 | 9

Player X, enter a number (1-9): 1

 X | 2 | 3
---+---+---
 4 | 5 | 6
---+---+---
 7 | 8 | 9

Player O, enter a number (1-9): 5
...

Player X wins!
```

---

