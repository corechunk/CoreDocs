# ↔️ Deque (Double-Ended Queue)

## 1. The Objective
A Deque (pronounced "deck") is a generalized version of a Queue that allows insertion and deletion from **both the front and the rear**. It can act as both a Stack and a Queue.

---

## 2. Visual Logic
### Bidirectional Access
```text
  FRONT <--> [ A | B | C | D ] <--> REAR
(Pop/Push)                      (Pop/Push)
```

### Flexibility
- **Stack Mode:** Push Front, Pop Front.
- **Queue Mode:** Push Rear, Pop Front.

---

## 3. The "Aha!" Moment
- **Versatility:** Deque is the "Swiss Army Knife" of linear structures. It is the underlying structure for `std::stack` and `std::queue` in C++ because it provides $O(1)$ operations at both ends.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (STL Deque)

```cpp
#include <iostream>
#include <deque>

int main() {
    std::deque<int> dq;

    dq.push_back(10);  // [10]
    dq.push_front(20); // [20, 10]
    dq.push_back(30);  // [20, 10, 30]

    std::cout << "Front: " << dq.front() << std::endl;
    std::cout << "Back: " << dq.back() << std::endl;

    dq.pop_front();
    std::cout << "New Front: " << dq.front() << std::endl;

    return 0;
}
```

---
[➔ Back to Queue Hub](queue.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
