## Experiment 1: Python Fundamentals for Computational Mathematics

### Aim
Introduce core Python control structures, functions, lists, file operations, and exception handling through foundational mathematical routines.

### Theory & Computational Context
Before invoking symbolic algebra or tensor libraries, an engineer must understand how loops, conditional statements, and functions approximate mathematical series $e^x \approx \sum_{n=0}^{N-1} \frac{x^n}{n!}$ —such as the Maclaurin expansion 
 
—and how exception handling prevents division-by-zero singularities during numerical iteration.

## Core Python Constructs

```python
# Student Identification Seed (Enter last 2 digits of your Roll Number)
ROLL_SEED = 42  # Modify this value (e.g., 01 to 99)

# 1. Hello World & Basic Arithmetic Operations
print("Hello, Computational Engineering World!")
a = 5 + (ROLL_SEED % 4)
b = 3
print(f"Inputs: a = {a}, b = {b}")
print("Addition (a + b):", a + b)
print("Subtraction (a - b):", a - b)
print("Multiplication (a * b):", a * b)
print("Exact Float Division (a / b):", round(a / b, 4))

# 2. Variables, Data Types & Lists
x_int = 10
y_float = 3.14159
z_str = "Vector_Calculus"
print(f"Types -> Integer: {x_int}, Float: {y_float}, String: {z_str}")

solver_methods = ["Euler", "Heun", "Runge-Kutta"]
solver_methods.append("SymPy_Exact")
solver_methods.remove("Heun")
print("Active Solver List:", solver_methods, "| First Element:", solver_methods[0])

# 3. Loops, Conditionals & Mathematical Functions
def evaluate_maclaurin_exp(x_val, terms=6):
    """Computes partial sums of e^x using a for-loop and conditional checks."""
    partial_sums = []
    running_sum = 0.0
    fact = 1.0
    for n in range(terms):
        if n > 0:
            fact *= n
        running_sum += (x_val ** n) / fact
        partial_sums.append(round(running_sum, 6))
    return partial_sums

x_test = 1.0 + (ROLL_SEED % 5) * 0.1
approx_history = evaluate_maclaurin_exp(x_test, terms=6)
print(f"Maclaurin Partial Sums for e^({x_test:.1f}):", approx_history)

# Conditional stability check on auxiliary discriminant
discriminant = (a ** 2) - 4 * b
if discriminant > 0:
    print(f"Discriminant ({discriminant}) > 0: Overdamped (Real & Distinct Roots)")
elif discriminant == 0:
    print("Discriminant == 0: Critically Damped (Repeated Real Roots)")
else:
    print("Discriminant < 0: Underdamped (Complex Conjugate Roots)")

# 4. Virtual File Read/Write & Exception Handling
with open("lab_log.txt", "w") as f:
    f.write(f"Roll Seed: {ROLL_SEED}\nFinal Series Approx: {approx_history[-1]}")

with open("lab_log.txt", "r") as f:
    print("Saved File Log ->", f.read().replace("\n", " | "))

try:
    singularity_check = 10.0 / 0.0
except ZeroDivisionError:
    print("Exception Handled: Division by zero prevented in stiffness ratio.")
finally:
    print(f"[Ex 1 Checksum | Seed {ROLL_SEED}] Completed successfully.")
```

