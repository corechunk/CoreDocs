# 🔄 Circular Queue

## 1. The Objective
A Circular Queue is an extended version of a regular queue where the last position is connected back to the first position. This solves the **"Memory Wastage"** problem of simple array-based queues where empty spaces at the front cannot be reused.

---

## 2. Visual Logic
### The Circular Loop
```text
      [ 0 | 1 | 2 | 3 | 4 ]
        ^               |
        |_______________|
```
- **Front:** Points to the first element.
- **Rear:** Points to the last element.
- **Connection:** `rear = (rear + 1) % size`

---

## 3. The "Aha!" Moment
- **Modulo Magic:** The `%` operator is the heart of circularity. It keeps the index within bounds and wraps it around automatically.
- **Efficient Reuse:** You never need to shift elements forward (like in a vector) to reuse space.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Circular Queue)

```cpp
#include <iostream>

class CircularQueue {
    int *arr;
    int front, rear, size;

public:
    CircularQueue(int s) {
        size = s;
        arr = new int[size];
        front = rear = -1;
    }

    void enqueue(int val) {
        if ((rear + 1) % size == front) return; // Full
        if (front == -1) front = 0;
        rear = (rear + 1) % size;
        arr[rear] = val;
    }

    void dequeue() {
        if (front == -1) return; // Empty
        if (front == rear) front = rear = -1;
        else front = (front + 1) % size;
    }

    int getFront() {
        if (front == -1) return -1;
        return arr[front];
    }
};

int main() {
    CircularQueue q(5);
    q.enqueue(10);
    q.enqueue(20);
    q.enqueue(30);
    
    std::cout << "Front: " << q.getFront() << std::endl;
    q.dequeue();
    std::cout << "Front after dequeue: " << q.getFront() << std::endl;
    
    return 0;
}
```

---
[➔ Back to Queue Hub](queue.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
