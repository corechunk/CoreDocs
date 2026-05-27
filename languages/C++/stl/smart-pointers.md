# 🧠 STL Smart Pointers (Ownership) - Master Reference

## 1. The Objective
Smart pointers are class templates that manage a raw pointer. They provide **Automatic Memory Management** using the RAII (Resource Acquisition Is Initialization) principle, ensuring that memory is deleted when the pointer goes out of scope.

---

## 2. Visual Logic
### Ownership Models
- **`unique_ptr`:** Only ONE owner. No copying allowed. (Like a personal key).
- **`shared_ptr`:** MULTIPLE owners. Deletes only when the last owner is gone. (Like a shared apartment).
- **`weak_ptr`:** Observer. Doesn't affect deletion. (Like a guest).

---

## 3. # The Logic Bridge (Key Points)

- **Performance:** `unique_ptr` has ZERO overhead compared to a raw pointer. `shared_ptr` has a small overhead due to the "Reference Count" (Control Block).
- **Rule of Thumb:** Use `unique_ptr` by default. Only upgrade to `shared_ptr` if multiple objects truly need to co-own the resource.
- **Cycles:** If two `shared_ptr` objects point to each other, they will **never** be deleted (Memory Leak). Use `weak_ptr` to break these cycles.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <memory>
#include <vector>

struct Resource {
    int id;
    Resource(int i) : id(i) { std::cout << "Created " << id << "\n"; }
    ~Resource() { std::cout << "Destroyed " << id << "\n"; }
};

int main() {
    // --- 1. UNIQUE_PTR ---
    auto u1 = std::make_unique<Resource>(1);
    // std::unique_ptr<Resource> u2 = u1; // ERROR: Cannot copy
    auto u2 = std::move(u1);              // Transfer ownership

    // --- 2. SHARED_PTR ---
    auto s1 = std::make_shared<Resource>(2);
    {
        auto s2 = s1;                     // Share ownership
        std::cout << "Count: " << s1.use_count() << "\n"; // 2
    }
    std::cout << "Count after scope: " << s1.use_count() << "\n"; // 1

    // --- 3. WEAK_PTR ---
    std::weak_ptr<Resource> w1 = s1;
    if (auto shared = w1.lock()) {        // Check if resource still exists
        std::cout << "Resource " << shared->id << " is still alive\n";
    }

    return 0;
} // Everything is automatically deleted here
```

---
[➔ Back to STL Hub](00-stl-overview.md)
