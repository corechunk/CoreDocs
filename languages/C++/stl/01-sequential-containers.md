# 📦 STL Containers (Sequential)

## 1. The Objective
Sequential containers store elements in a strictly linear order. They allow you to choose between fast access at any position or efficient insertion at the ends or middle.

---

## 2. Visual Logic
### The Sequential Spectrum
- **`array`:** Fixed-size stack block.
- **`vector`:** Dynamic-size heap block.
- **`deque`:** Segmented blocks (Fast ends).
- **`list`:** Doubly linked nodes.
- **`forward_list`:** Singly linked nodes.

---

## 3. # The Logic Bridge (Key Points)

### Complexity Comparison
| Container | Random Access | Insert/Delete (Ends) | Insert/Delete (Middle) |
| :--- | :---: | :---: | :---: |
| `vector` | $O(1)$ | $O(1)$ amortized | $O(n)$ |
| `deque` | $O(1)$ | $O(1)$ | $O(n)$ |
| `list` | $O(n)$ | $O(1)$ | $O(1)$ |
| `array` | $O(1)$ | N/A | N/A |

### Iterator Invalidation Rules
- **`vector`:** All iterators invalid on reallocation; pointers to moved elements invalid on insertion/deletion.
- **`deque`:** All iterators invalid on any insertion/deletion (except pointers to elements themselves remain valid if only ends are modified).
- **`list`:** Iterators **remain valid** regardless of other insertions/deletions.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Abstract Example)

```cpp
#include <iostream>
#include <vector>
#include <deque>
#include <list>

int main() {
    std::vector v = {1, 2};
    std::deque d = {3, 4};
    std::list l = {5, 6};

    std::cout << "Sequential pillars initialized." << std::endl;
    return 0;
}
```

---

## 🔗 Granular Sub-Topics

### Base Containers
- [std::vector](vector.md) - The standard dynamic array (Full API).
- [std::list](list.md) - Doubly linked flexibility (Splice/Merge).
- [std::deque](deque.md) - Double-ended efficiency.
- [std::array](array.md) - Zero-overhead fixed size.
- [std::forward_list](forward_list.md) - Singly linked minimalist.

### Container Adapters
- [std::stack](stack.md) - LIFO logic wrapper.
- [std::queue](queue.md) - FIFO logic wrapper.
- [std::priority_queue](priority_queue.md) - Heap-based ordering.

[➔ Back to STL Hub](00-stl-overview.md)
