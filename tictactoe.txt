# 5:34 AM 2/6/2024

import tkinter as tk
import random

class TicTacToe:
    def __init__(self, root):
        self.root = root
        self.root.title("Tic Tac Toe")
        self.root.geometry("300x300")
        self.current_player = "X"
        self.board = [""] * 9

        self.buttons = []
        for i in range(3):
            for j in range(3):
                button = tk.Button(root, text="", font=("Helvetica", 16), width=6, height=3,
                                   command=lambda row=i, col=j: self.make_move(row, col))
                button.grid(row=i, column=j)
                self.buttons.append(button)

    def make_move(self, row, col):
        index = 3 * row + col
        if self.board[index] == "":
            self.board[index] = self.current_player
            self.buttons[index].config(text=self.current_player, state=tk.DISABLED)
            if self.check_winner():
                self.display_winner()
            elif "" not in self.board:
                self.display_tie()
            else:
                self.switch_player()
                self.computer_move()

    def computer_move(self):
        empty_cells = [i for i, val in enumerate(self.board) if val == ""]
        if empty_cells:
            index = random.choice(empty_cells)
            self.board[index] = self.current_player
            self.buttons[index].config(text=self.current_player, state=tk.DISABLED)
            if self.check_winner():
                self.display_winner()
            elif "" not in self.board:
                self.display_tie()
            else:
                self.switch_player()

    def check_winner(self):
        winning_combinations = [(0, 1, 2), (3, 4, 5), (6, 7, 8),
                                (0, 3, 6), (1, 4, 7), (2, 5, 8),
                                (0, 4, 8), (2, 4, 6)]

        for combo in winning_combinations:
            if self.board[combo[0]] == self.board[combo[1]] == self.board[combo[2]] != "":
                return True
        return False

    def display_winner(self):
        winner_label = tk.Label(self.root, text=f"Player {self.current_player} wins!", font=("Helvetica", 14))
        winner_label.grid(row=3, column=0, columnspan=3)
        self.disable_buttons()

    def display_tie(self):
        tie_label = tk.Label(self.root, text="It's a tie!", font=("Helvetica", 14))
        tie_label.grid(row=3, column=0, columnspan=3)
        self.disable_buttons()

    def disable_buttons(self):
        for button in self.buttons:
            button.config(state=tk.DISABLED)

    def switch_player(self):
        self.current_player = "O" if self.current_player == "X" else "X"


def center_window(window, width, height):
    screen_width = window.winfo_screenwidth()
    screen_height = window.winfo_screenheight()

    x = (screen_width - width) // 2
    y = (screen_height - height) // 2

    window.geometry(f"{width}x{height}+{x}+{y}")


if __name__ == "__main__":
    root = tk.Tk()
    center_window(root, 300, 300)
    game = TicTacToe(root)
    root.mainloop()
