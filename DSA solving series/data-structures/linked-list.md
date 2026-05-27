# 🔗 Linked Lists (Non-Contiguous Memory)

## 1. The Objective
A Linked List is a linear data structure where elements are not stored in contiguous memory locations. Instead, each element is a **Node** that contains its own data and a **Pointer** (reference) to the next node in the sequence.

---

## 2. Visual Logic
### The Node Structure
```text
[ Data | Pointer ] -> [ Data | Pointer ] -> [ Data | NULL ]
```

### Contiguous (Array) vs. Linked (List)
- **Array:** `[A][B][C][D]` (Fixed size, instant access, slow insert/delete).
- **Linked List:** `[A]->[B]->[C]->[D]` (Dynamic size, slow access, instant insert/delete if position is known).

---

## 3. The "Aha!" Moment
- **Memory Flexibility:** Linked Lists grow and shrink at runtime without needing to reallocate or shift the entire data set.
- **Pointer Power:** Insertion at the beginning is $O(1)$ because you only need to change one pointer, whereas an array requires $O(n)$ to shift all elements.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Abstract Node)

```cpp
#include <iostream>

/**
 * Basic structure for a Singly Linked Node.
 */
struct Node {
    int data;
    Node* next;

    Node(int val) : data(val), next(nullptr) {}
};

void printList(Node* head) {
    while (head) {
        std::cout << head->data << " -> ";
        head = head->next;
    }
    std::cout << "NULL" << std::endl;
}

int main() {
    Node* head = new Node(10);
    head->next = new Node(20);
    head->next->next = new Node(30);

    std::cout << "Linked List Visualization:" << std::endl;
    printList(head);
    
    return 0;
}
```

---

## 🔗 Sub-Topics (Specific Linked Structures)
- [Singly Linked List](singly-linked-list.md) - One-way pointers.
- [Doubly Linked List](doubly-linked-list.md) - Two-way pointers (Prev & Next).
- [Circular Linked List](circular-linked-list.md) - Last node points to Head.
- [Fast & Slow Pointers](../algorithms/fast-and-slow-pointers.md) - Cycle detection & Mid-point logic.

[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
