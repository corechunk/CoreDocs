# 🔁 Recursion

## 1. The Objective
Recursion is a problem-solving technique where a function calls itself to solve a smaller version of the same problem. It is the core engine for **Trees**, **Graphs**, and **Dynamic Programming**.

---

## 2. Visual Logic
### The Call Stack
```text
Call: fact(3)
  -> Call: fact(2)
    -> Call: fact(1)
      -> Return: 1
    -> Return: 2 * 1
  -> Return: 3 * 2
Result: 6
```

---

## 3. The Logic Bridge
- **The "Base Case" Safety:** Every recursive function **must** have a base case (an exit condition) to prevent infinite loops and `StackOverflow` errors.
- **Trust the Subproblem:** The key to writing recursion is "Leap of Faith". Assume the recursive call works for $N-1$, and focus only on how to use that result to solve for $N$.
- **Memory Cost:** Every call consumes memory on the **Stack**. Too much recursion leads to crashes, which is why we often optimize with **Tail Recursion** or **Iteration**.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Factorial)

```cpp
#include <iostream>

// Standard Recursion
long long factorial(int n) {
    if (n <= 1) return 1; // Base Case
    return n * factorial(n - 1); // Recursive Step
}

int main() {
    int n = 5;
    std::cout << "Factorial of " << n << " is " << factorial(n) << std::endl;
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
