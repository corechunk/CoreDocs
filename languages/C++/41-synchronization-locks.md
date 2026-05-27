# 🔴 Standard: Synchronization [SYSTEMS]

## Definition
Managing shared data access using `std::mutex` and **Atomics** to prevent race conditions.

## 1. Legacy Way (C++11 / C++17)
Manual lock management.

```cpp
#include <iostream>
#include <mutex>

int counter = 0;
std::mutex mtx;

int main() {
    mtx.lock();
    counter++;
    mtx.unlock();
    
    std::cout << counter << "\n"; // Output: 1
    return 0;
}
```

## 2. Modern Way (C23)
Using **`std::lock_guard`** (RAII) and **`std::atomic`**.

```cpp
#include <iostream>
#include <mutex>
#include <atomic>

std::atomic<int> counter = 0;

int main() {
    // Atomic: Thread-safe without manual locks
    counter++; 
    
    std::cout << counter.load() << "\n"; // Output: 1
    return 0;
}
```

# The Logic Bridge
// Logic: `std::atomic` uses CPU-level instructions (like `LOCK INC`) to perform operations in a single, uninterruptible step, bypassing the need for heavy Kernel-level mutexes.
