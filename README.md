import tkinter as tk
class WeightWidget(tk.Frame):
    def __init__(self, master, initial_weight=50, **kwargs):
        super().__init__(master, **kwargs)
        self.weight = tk.IntVar(value=initial_weight)
        self.create_widgets()
    def create_widgets(self):
        self.scale = tk.Scale(self, variable=self.weight, from_=0, to=100, orient="horizontal", length=200, tickinterval=10)
        self.scale.pack(pady=5)

        self.weight_label = tk.Label(self, text=f"Weight: {self.weight.get()} kg", font=("Arial", 14))
        self.weight_label.pack()

        self.scale.bind("<ButtonRelease-1>", self.on_scale_change)
        self.pack()
    def get_weight(self):
        return self.weight.get()
    def set_weight(self, weight):
        self.weight.set(weight)
        self.weight_label.config(text=f"Weight: {self.weight.get()} kg")
    def on_scale_change(self, event):
        self.weight_label.config(text=f"Weight: {self.weight.get()} kg")
    def get_weight_in_lbs(self):
        return self.weight.get() * 2.20462
# Create main window
root = tk.Tk()
root.title("Weight Widget")
# Create weight widget
weight_widget = WeightWidget(root)
weight_widget.pack(pady=20)
# Get current weight
current_weight = weight_widget.get_weight()
print(f"Current weight: {current_weight} kg")
print(f"Current weight: {weight_widget.get_weight_in_lbs()} lbs")
# Set weight to 75 kg
weight_widget.set_weight(75)
# Run the event loop
root.mainloop()
Sent 12m ago
Messages are missing. Sync now
Write to Imae Joy Acuna
