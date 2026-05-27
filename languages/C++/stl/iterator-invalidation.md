# ⚠️ STL Iterator Invalidation

## 1. The Objective
Iterator Invalidation occurs when an operation on a container (like adding or removing elements) makes existing iterators, pointers, or references to its elements "stale" or "unsafe". Using an invalidated iterator leads to **Undefined Behavior (Crash)**.

---

## 2. Visual Logic
### Vector Reallocation
```text
Step 1: [ A | B | C ] (Capacity: 3)  Iter it -> B
Step 2: push_back(D) -> Resize!
Step 3: New block [ A | B | C | D | _ ]
         Old block [ (Trash) ]
         it -> (Points to garbage in old memory)
```

---

## 3. The Logic Bridge
- **Rule of Thumb (Vector/Deque):** Any operation that changes the size can potentially invalidate all iterators (if capacity is exceeded).
- **Rule of Thumb (List/Map/Set):** Iterators are only invalidated for the specific element being **erased**. All other iterators remain perfectly safe.
- **The "Safe" Way:** In Modern C++, algorithms like `std::erase_if` handle the invalidation logic for you, making manual loops much safer.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (The Crash Loop)

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector v = {1, 2, 3};
    auto it = v.begin(); // Points to 1

    v.push_back(4); 
    v.push_back(5); // Likely triggers reallocation

    // DANGEROUS: 'it' might be invalidated here!
    // std::cout << *it << std::endl; 

    // Proper way: Re-assign after modification
    it = v.begin();
    std::cout << "Safe: " << *it << std::endl;

    return 0;
}
```

---
[➔ Back to Iterators Hub](03-iterators.md)
