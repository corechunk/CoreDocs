# 🔴 Standard: Storage Classes [SYSTEMS]

## Definition
Storage classes define the persistence and linkage. Modern C++ uses `thread_local` and `static` to manage state across time and threads.

## 1. Legacy Way (C++11 / C++17)
Standard `static` and `extern` usage.

```cpp
#include <iostream>

void counter() {
    static int calls = 0; // Stays alive between calls
    calls++;
    std::cout << "Calls: " << calls << "\n";
}

int main() {
    counter(); // Output: Calls: 1
    counter(); // Output: Calls: 2
    return 0;
}
```

## 2. Modern Way (C23)
Using `thread_local` and attributes for linkage optimization.

```cpp
#include <iostream>

// thread_local: Unique for each execution thread
thread_local int thread_id = 1;

int main() {
    static int app_state = 0;
    app_state++;
    
    std::cout << "State: " << app_state << "\n"; // Output: State: 1
    return 0;
}
```

# The Logic Bridge
// Logic: `static` objects are initialized only once. Their address remains constant throughout the program's execution, residing in the binary's BSS or Data segment.
