# Tic-Tac-Toe-in-Python

This is a simple implementation of the classic Tic Tac Toe game using Python and Tkinter. The game features a basic GUI that allows two players to take turns making moves. The computer player (O) makes random moves in response to the player's moves (X). The game ends when one player wins, there is a tie, or the player chooses to exit the application.

How to :
• Clone or download this repository to your local machine.
• Run the tictactoe.py file using a Python interpreter.
• The game window will appear, and you can take turns with the computer player to make moves on the Tic Tac Toe board.

Game Rules:
• The game is played on a 3x3 grid.
• Players take turns to place their symbol (X or O) on an empty cell.
• The first player to get three of their symbols in a row (horizontally, vertically, or diagonally) wins.
• If all cells are filled and no player has won, the game is a tie.

Implementation Details:
• The game is implemented in Python using the Tkinter library for the GUI.
• Players can click on the empty cells to make their moves.
• The computer player (O) makes random moves in response to the player's moves.
• The game checks for a winner or a tie after each move.

Code Structure:
• tictactoe.py contains the main implementation of the game.
• The TicTacToe class encapsulates the game logic and GUI elements.
• The game is started by creating an instance of the TicTacToe class and running the Tkinter main loop.
