# 🧵 STL Concurrency - Master Reference

## 1. The Objective
The Concurrency library allows C++ programs to perform multiple tasks at the same time. This ranges from low-level thread management to high-level **Parallel Algorithms** that use multiple CPU cores automatically.

---

## 2. Visual Logic
### The Parallel Pipeline
```text
[ Data ] -> [ Policy: execution::par ] -> [ Algorithm ]
      |             |                    |
      |----Core 1---|                    |
      |----Core 2---|                    |
      |----Core 3---|--------------------> [ Result ]
```

---

## 3. # The Logic Bridge (Key Points)

- **`std::jthread` (C++20):** A "joining thread" that automatically joins (waits for finish) when it goes out of scope, preventing the common "forgot to join" crashes.
- **Atomics:** Use `std::atomic<int>` for simple counters shared between threads. They are lock-free and much faster than using a `mutex`.
- **Parallel Algos (C++17):** You can pass an execution policy to almost any STL algorithm (e.g., `std::sort(std::execution::par, v.begin(), v.end())`).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <thread>
#include <atomic>
#include <vector>
#include <algorithm>
#include <execution> // C++17 Parallel Policies

int main() {
    // --- 1. ATOMICS (Safe sharing) ---
    std::atomic<int> counter = 0;

    // --- 2. JTHREAD (C++20 Auto-join) ---
    std::jthread t([&counter]() {
        for(int i=0; i<100; i++) counter++;
    });

    // --- 3. PARALLEL ALGORITHM ---
    std::vector<int> v(1000000, 1);
    std::sort(std::execution::par, v.begin(), v.end());

    std::cout << "Counter: " << counter << "\n";
    return 0;
}
```

---
[➔ Back to STL Hub](00-stl-overview.md)
