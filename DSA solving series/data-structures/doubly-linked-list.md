# 🔗 Doubly Linked List (DLL)

## 1. The Objective
A Doubly Linked List (DLL) is a complex type of linked list where each node contains pointers to both the **next** node and the **previous** node. This allows for bidirectional traversal and more efficient deletion operations.

---

## 2. Visual Logic
### Bidirectional Node
```text
[ Prev | Data | Next ] <=> [ Prev | Data | Next ] <=> [ Prev | Data | Next ]
```

### Insertion Logic (Middle)
1. **New Node (N):** Point `N->next` to `Current` and `N->prev` to `Current->prev`.
2. **Current's Prev (P):** Point `P->next` to `N`.
3. **Current:** Point `Current->prev` to `N`.

---

## 3. The "Aha!" Moment
- **Delete Power:** Unlike a Singly Linked List where you need the *predecessor* to delete a node, in a DLL, you can delete a node $O(1)$ if you have a reference to the node itself (because it knows its own predecessor).
- **Space-Time Tradeoff:** You gain bidirectional power but use more memory (two pointers per node) and have more complex maintenance during insertions/deletions.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Core DLL)

```cpp
#include <iostream>

struct Node {
    int data;
    Node *next, *prev;
    Node(int val) : data(val), next(nullptr), prev(nullptr) {}
};

class DoublyLinkedList {
public:
    Node *head, *tail;
    DoublyLinkedList() : head(nullptr), tail(nullptr) {}

    void insertTail(int val) {
        Node* newNode = new Node(val);
        if (!head) {
            head = tail = newNode;
            return;
        }
        tail->next = newNode;
        newNode->prev = tail;
        tail = newNode;
    }

    void displayForward() {
        Node* temp = head;
        while (temp) {
            std::cout << temp->data << " <-> ";
            temp = temp->next;
        }
        std::cout << "NULL" << std::endl;
    }
};

int main() {
    DoublyLinkedList list;
    list.insertTail(10);
    list.insertTail(20);
    list.insertTail(30);

    std::cout << "DLL Forward: ";
    list.displayForward();

    return 0;
}
```

---
[➔ Back to Linked List Hub](linked-list.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
