# 👥 Queues (FIFO: First-In, First-Out)

## 1. The Objective
A Queue is a linear data structure that follows the **First-In, First-Out (FIFO)** principle. It behaves like a real-world queue (line): the first person to join the line is the first one served.

---

## 2. Visual Logic
### The "Line" Analogy
```text
IN -> [ D | C | B | A ] -> OUT
      (Rear)       (Front)
```

### Core Operations
- **Enqueue:** Add to the Rear.
- **Dequeue:** Remove from the Front.
- **Front:** Peek at the first element.

---

## 3. The "Aha!" Moment
- **Fairness:** Queues are the most "fair" data structure, processing items in the exact order they arrive (e.g., Printer queues, CPU task scheduling).
- **Buffer Power:** Queues act as buffers between asynchronous processes (e.g., IO buffers).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Manual Queue)

```cpp
#include <iostream>
#define MAX 100

class Queue {
    int front, rear;
    int arr[MAX];

public:
    Queue() : front(0), rear(0) {}

    void enqueue(int x) {
        if (rear == MAX) return;
        arr[rear++] = x;
    }

    void dequeue() {
        if (front == rear) return;
        front++;
    }

    int getFront() {
        if (front == rear) return -1;
        return arr[front];
    }
};

int main() {
    Queue q;
    q.enqueue(10);
    q.enqueue(20);
    q.enqueue(30);

    std::cout << "Front element: " << q.getFront() << std::endl;
    q.dequeue();
    std::cout << "Front element after dequeue: " << q.getFront() << std::endl;

    return 0;
}
```

---

## 🔗 Sub-Topics (Specific Queue Types)
- [Circular Queue](circular-queue.md) - Efficient space reuse.
- [Deque (Double-Ended Queue)](deque.md) - Insertion/Deletion at both ends.
- [Priority Queue](priority-queue.md) - Order based on importance.

[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
