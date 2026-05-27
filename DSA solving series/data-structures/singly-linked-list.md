# 🔗 Singly Linked List (SLL)

## 1. The Objective
A Singly Linked List (SLL) is the simplest form of linked list where each node points only to the **next** node. It is highly efficient for head-heavy operations and dynamic memory growth.

---

## 2. Visual Logic
### Pointer Reassignment (Insertion at Head)
1. **New Node:** `[5 | NULL]`
2. **Point to Head:** `[5 | *next] -> [Current Head]`
3. **Update Head:** `Head = [5]`

### Traversal Logic
- Start at `head`.
- While `current != NULL`, move to `current->next`.

---

## 3. The "Aha!" Moment
- **Directional Constraint:** You can only go forward. To find the previous node, you must traverse from the head (or use a Doubly Linked List).
- **The "Tail" Trick:** Maintaining a `tail` pointer turns $O(n)$ end-insertions into $O(1)$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Core SLL)

```cpp
#include <iostream>

struct Node {
    int data;
    Node* next;
    Node(int val) : data(val), next(nullptr) {}
};

class SinglyLinkedList {
public:
    Node* head;
    SinglyLinkedList() : head(nullptr) {}

    // O(1) Insertion
    void insertHead(int val) {
        Node* newNode = new Node(val);
        newNode->next = head;
        head = newNode;
    }

    void display() {
        Node* temp = head;
        while (temp) {
            std::cout << temp->data << " -> ";
            temp = temp->next;
        }
        std::cout << "NULL" << std::endl;
    }
};

int main() {
    SinglyLinkedList list;
    list.insertHead(30);
    list.insertHead(20);
    list.insertHead(10);

    std::cout << "SLL Display: ";
    list.display();

    return 0;
}
```

---
[➔ Back to Linked List Hub](linked-list.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
