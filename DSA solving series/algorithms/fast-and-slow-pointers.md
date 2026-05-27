# 🐢🐇 Fast & Slow Pointers

## 1. The Objective
The Fast & Slow Pointers technique (also known as the **Hare and Tortoise** algorithm) uses two pointers that move through a data structure at different speeds. It is primarily used for **detecting cycles** and finding the **middle** of a linked list.

---

## 2. Visual Logic
### Cycle Detection (Floyd's)
```text
[A] -> [B] -> [C] -> [D]
               ^      |
               |______|
```
- **Tortoise:** Moves 1 step at a time.
- **Hare:** Moves 2 steps at a time.
- **Result:** If there is a cycle, the Hare will eventually lap the Tortoise and they will meet. If there is no cycle, the Hare will reach `NULL`.

---

## 3. The Logic Bridge
- **The Relative Speed:** By moving at different speeds, we create a relative velocity between the pointers. If they are in a loop, the distance between them shrinks by 1 at every step until it becomes 0 (meeting point).
- **The Middle Trick:** When the Fast pointer reaches the end of a list ($N$), the Slow pointer will be at exactly $N/2$. This is a one-pass way to find the midpoint without counting elements first.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Cycle Detection)

```cpp
#include <iostream>

struct Node {
    int data;
    Node* next;
    Node(int val) : data(val), next(nullptr) {}
};

bool hasCycle(Node* head) {
    Node *slow = head, *fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) return true;
    }
    return false;
}

int main() {
    Node* head = new Node(1);
    head->next = new Node(2);
    head->next->next = head; // Cycle!

    std::cout << "Has Cycle: " << hasCycle(head) << std::endl;
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
