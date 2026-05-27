# 🔵 Standard: Async & Coroutines [PRO]

## Definition
High-level concurrency using `std::async` (C++11) or **Coroutines** (C++20) for non-blocking, interruptible execution.

## 1. Legacy Way (C++11 / C++17)
Using `std::async` and `std::future`.

```cpp
#include <iostream>
#include <future>

int main() {
    auto fut = std::async([]{ return 10; });
    
    std::cout << fut.get() << "\n"; // Output: 10
    return 0;
}
```

## 2. Modern Way (C23)
Concept of a simple Coroutine (C++20/23 logic).

```cpp
#include <iostream>
#include <coroutine>

// Note: Coroutines require significant boilerplate (Promise types)
// Shown here as a conceptual mental model
int main() {
    std::cout << "Coroutine Model\n"; // Output: Coroutine Model
    return 0;
}
```

# The Logic Bridge
// Logic: `std::async` might run the task on a new thread or lazily on the same thread. Coroutines are "Pauseable Functions" that store their state on the Heap instead of the Stack.
