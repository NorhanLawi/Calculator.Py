



import tkinter as tk

class CalculatorGUI:
    def __init__(self, root):
        self.root = root
        self.root.title("Simple Calculator")

        self.entry = tk.Entry(root, width=20)
        self.entry.grid(row=0, column=0, columnspan=4)

        buttons = [
            '7', '8', '9', '/',
            '4', '5', '6', '*',
            '1', '2', '3', '-',
            '0', '.', '=', '+'
        ]

        row_num = 1
        col_num = 0

        for button_text in buttons:
            self.create_button(button_text, row_num, col_num)
            col_num += 1
            if col_num > 3:
                col_num = 0
                row_num += 1

    def create_button(self, text, row, col):
        button = tk.Button(self.root, text=text, command=lambda: self.button_click(text))
        button.grid(row=row, column=col, padx=5, pady=5)

    def button_click(self, text):
        if text == '=':
            try:
                result = eval(self.entry.get())
                self.entry.delete(0, tk.END)
                self.entry.insert(0, result)
            except Exception as e:
                self.entry.delete(0, tk.END)
                self.entry.insert(0, "Error")
        else:
            self.entry.insert(tk.END, text)

if __name__ == "__main__":
    root = tk.Tk()
    calculator = CalculatorGUI(root)
    root.mainloop()




