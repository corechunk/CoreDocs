# 📦 STL Containers (Sequential)

## 1. The Objective
Sequential containers store elements in a strictly linear order. They allow you to choose between fast access at any position (Vectors) or fast insertion/deletion at the ends (Deque/List).

---

## 2. Visual Logic
- **`std::vector`:** `[A][B][C][D][ ]` - Contiguous, like an array. Fast random access.
- **`std::deque`:** `[ ][A][B][C][D][ ]` - Double-ended queue. Fast at both ends.
- **`std::list`:** `[A]<->[B]<->[C]` - Doubly linked list. Fast insert/delete anywhere if iterator is known.

---

## 3. The Logic Bridge
- **The Choice:** Use `vector` by default. It has the best cache locality. Only use `list` if you are doing massive middle-insertions. Only use `deque` if you need to push/pop from both ends frequently.
- **Modern Performance:** In Modern C++, `vector`'s contiguous memory is so fast that it often outperforms `list` even for middle operations on smaller data sets due to CPU cache efficiency.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Vector vs List)

```cpp
#include <iostream>
#include <vector>
#include <list>

int main() {
    // Modern CTAD (Template Argument Deduction)
    std::vector v = {1, 2, 3}; 
    v.push_back(4);

    std::list l = {10, 20, 30};
    l.push_front(5);

    std::cout << "Vector: ";
    for(auto x : v) std::cout << x << " ";
    
    std::cout << "\nList: ";
    for(auto x : l) std::cout << x << " ";
    
    return 0;
}
```

---
[➔ Back to STL Hub](00-stl-overview.md)
