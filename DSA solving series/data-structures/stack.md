# 📚 Stacks (LIFO: Last-In, First-Out)

## 1. The Objective
A Stack is a linear data structure that follows the **Last-In, First-Out (LIFO)** principle. It behaves like a physical stack of plates: the last plate placed on top is the first one to be removed.

---

## 2. Visual Logic
### The "Bucket" Analogy
```text
|   D   |  <-- TOP (Last In)
|   C   |
|   B   |
|___A___|  <-- BOTTOM (First In)
```

### Core Operations
- **Push:** Add to the Top.
- **Pop:** Remove from the Top.
- **Peek:** Look at the Top without removing.

---

## 3. The "Aha!" Moment
- **Natural Reversing:** Because of LIFO, a stack naturally reverses data (e.g., String reversal, Undo/Redo operations).
- **Execution Management:** Compilers use a "Call Stack" to manage function calls and local variables.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Manual Stack)

```cpp
#include <iostream>
#define MAX 100

class Stack {
    int top;
    int arr[MAX];

public:
    Stack() : top(-1) {}

    bool push(int x) {
        if (top >= (MAX - 1)) return false;
        arr[++top] = x;
        return true;
    }

    int pop() {
        if (top < 0) return 0;
        return arr[top--];
    }

    int peek() {
        if (top < 0) return 0;
        return arr[top];
    }

    bool isEmpty() { return (top < 0); }
};

int main() {
    Stack s;
    s.push(10);
    s.push(20);
    s.push(30);

    std::cout << s.pop() << " popped from stack\n";
    std::cout << "Top element is : " << s.peek() << std::endl;

    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
