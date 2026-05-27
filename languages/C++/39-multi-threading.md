# 🔴 Standard: Multi-Threading [SYSTEMS]

## Definition
Concurrent execution using `std::thread` (C++11) or the safer `std::jthread` (C++20), which joins automatically upon destruction.

## 1. Legacy Way (C++11 / C++17)
Standard thread and manual join.

```cpp
#include <iostream>
#include <thread>

void task() { std::cout << "Running\n"; }

int main() {
    std::thread t(task);
    t.join(); // Must join or program crashes
    
    std::cout << "Finished\n"; // Output: Finished
    return 0;
}
```

## 2. Modern Way (C23)
Using **`std::jthread`** (Joinable Thread) for automatic lifecycle management.

```cpp
#include <iostream>
#include <thread> // Includes jthread since C++20

void task() { std::cout << "Running\n"; }

int main() {
    // jthread: Automatically joins on scope exit
    std::jthread t(task);
    
    std::cout << "Finished\n"; // Output: Finished
    return 0;
}
```

# The Logic Bridge
// Logic: Threads share the process address space. `std::jthread` uses RAII to ensure that the thread is either joined or detached before the object is destroyed, preventing "Dangling Threads."
