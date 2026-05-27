# 🔗 Circular Linked List (CLL)

## 1. The Objective
A Circular Linked List (CLL) is a variation of a linked list where the **last node points back to the first node**, forming a continuous loop. There is no `NULL` at the end of the list.

---

## 2. Visual Logic
### The Ring Structure
```text
      [ Head ] -> [ Node ] -> [ Node ]
         ^                       |
         |_______________________|
```

### Traversal Check
- In a normal list, you stop when `current == NULL`.
- In a CLL, you stop when `current->next == head`.

---

## 3. The "Aha!" Moment
- **No Dead Ends:** Useful for applications that need to go around the list repeatedly (e.g., Round Robin scheduling in OS, Multiplayer game turn management).
- **Access to Head:** From any node, you can reach the head without restarting from a global pointer.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Core CLL)

```cpp
#include <iostream>

struct Node {
    int data;
    Node* next;
    Node(int val) : data(val), next(nullptr) {}
};

class CircularLinkedList {
public:
    Node* head;
    CircularLinkedList() : head(nullptr) {}

    void insert(int val) {
        Node* newNode = new Node(val);
        if (!head) {
            head = newNode;
            newNode->next = head;
            return;
        }
        Node* temp = head;
        while (temp->next != head) temp = temp->next;
        temp->next = newNode;
        newNode->next = head;
    }

    void display() {
        if (!head) return;
        Node* temp = head;
        do {
            std::cout << temp->data << " -> ";
            temp = temp->next;
        } while (temp != head);
        std::cout << "(Back to Head)" << std::endl;
    }
};

int main() {
    CircularLinkedList list;
    list.insert(10);
    list.insert(20);
    list.insert(30);

    std::cout << "CLL Display: ";
    list.display();

    return 0;
}
```

---
[➔ Back to Linked List Hub](linked-list.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
