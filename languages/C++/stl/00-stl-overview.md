# 🚀 C++ Standard Template Library (STL) Overview

## Definition
The **Standard Template Library (STL)** is a powerful collection of generic classes and functions in C++. It provides highly optimized data structures (Containers) and procedures (Algorithms) that work seamlessly together through Iterators.

---

## 1. The Four Pillars of STL

| Pillar | Purpose | Key Elements |
| :--- | :--- | :--- |
| **Containers** | Data Storage | `vector`, `map`, `unordered`, `stack` |
| **Algorithms** | Data Processing | `sort`, `ranges`, `execution::par` |
| **Iterators** | The "Glue" | `begin()`, `end()`, `ranges::sentinel` |
| **Functional** | Logic Injection | Lambdas, `std::function`, `std::bind` |
| **Smart Pointers** | Ownership | `unique_ptr`, `shared_ptr`, `weak_ptr` |
| **Views & Spans** | Fast Access | `std::span`, `std::string_view` |
| **Vocabulary** | Logic Safety | `optional`, `variant`, `expected` |
| **Concurrency** | Parallelism | `jthread`, `atomic`, `mutex`, `promise` |
| **Utilities** | Helper Tools | `pair`, `tuple`, `bitset`, `filesystem` |

---

## 2. Legacy vs. Modern STL

### 🏛️ Legacy Way (C++98 / 03)
Verbose syntax, manual iterator loops, and custom comparator structs.
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

// Legacy Comparator Struct
struct IsEven {
    bool operator()(int n) { return n % 2 == 0; }
};

int main() {
    std::vector<int> v;
    v.push_back(10); v.push_back(5); v.push_back(20);

    // Verbose Iterator Loop
    std::vector<int>::iterator it;
    for(it = v.begin(); it != v.end(); ++it) {
        std::cout << *it << " ";
    }

    // Manual Functor Usage
    int count = std::count_if(v.begin(), v.end(), IsEven());
    // Output: 10 5 20
}
```

### 🚀 Modern Way (C++20 / 23)
Clean syntax with `auto`, Range-based loops, Lambdas, and the `std::ranges` library.
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <ranges> // C++20

int main() {
    std::vector v = {10, 5, 20}; // CTAD (C++17)

    // Range-based Loop (Clean)
    for (const auto& x : v) std::cout << x << " ";

    // Inline Lambdas + Ranges (C++20)
    auto count = std::ranges::count_if(v, [](int n){ return n % 2 == 0; });
    
    // Projections (C++20) - Sorting by absolute value
    std::ranges::sort(v, {}, [](int n){ return std::abs(n); });
}
```

---

## # The Logic Bridge

### Why the Shift?
1. **Move Semantics (C++11):** Legacy STL relied on "Deep Copies" which were expensive for large containers. Modern STL uses "Move Semantics," transferring ownership of memory instead of duplicating it, leading to massive performance gains.
2. **Type Inference (`auto`):** Eliminates redundant boilerplate like `std::vector<std::pair<int, std::string>>::iterator`.
3. **Ranges Library (C++20):** In Legacy, algorithms required pairs of iterators `(v.begin(), v.end())`. Modern Ranges allow passing the entire container `(v)`, which is safer and prevents "iterator mismatch" bugs.
4. **Safety:** Smart pointers (`std::unique_ptr`) and `std::span` (C++20) provide modern ways to view and manage memory within STL containers without raw pointers.

---

## 🔗 Sub-Topics (The STL Spoke Files)
## 🔗 Sub-Topics (The STL Master Map)

### 1. Containers & Adapters
- [Sequential Containers](01-sequential-containers.md) - `vector`, `deque`, `list`, `array`.
- [Associative Containers](02-associative-containers.md) - `map`, `set`, `unordered`, `multi`.
- [Container Adapters](stack.md) - `stack`, `queue`, `priority_queue`.

### 2. Algorithms & Iterators
- [Algorithm Engine](04-algorithms.md) - Search, Sort, Ranges, Complexity.
- [Iterators Deep-Dive](03-iterators.md) - Categories, Invalidation, Sentinels.

### 3. Functional & Logic
- [Functional C++](05-functional.md) - Lambdas, `std::function`, Bind expressions.

### 4. Memory & Ownership
- [Smart Pointers](smart-pointers.md) - `unique_ptr`, `shared_ptr`, `weak_ptr`.
- [Memory Models](../../DSA-Master-Roadmap.md) - Allocation and Cache Locality.

### 5. Modern Data Access (C++17/20)
- [Views & Spans](views-and-spans.md) - Non-owning access to ranges.

### 6. Safety & Vocabulary
- [Vocabulary Types](vocabulary-types.md) - `optional`, `variant`, `any`, `expected`.

### 7. Concurrency & Systems
- [STL Concurrency](concurrency.md) - Threading, Atomics, Parallel Algorithms.
- [System Utilities](system-utils.md) - `filesystem`, `chrono`, `regex`.

### 8. Specialized Tools
- [Specialized Containers](bitset.md) - `bitset`.
- [Utility Structures](utility-containers.md) - `pair`, `tuple`.

[➔ Back to C++ Hub](../master-cpp.md) | [➔ Back to Roadmap](../../DSA-Master-Roadmap.md)
