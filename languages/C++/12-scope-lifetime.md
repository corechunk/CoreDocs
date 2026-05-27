# 🟢 Standard: Scope & Lifetime [CORE]

## Definition
C++ uses **RAII** (Resource Acquisition Is Initialization), where the lifetime of a resource is tied to the scope of an object. Curly braces `{}` define both visibility and the automatic destruction of objects.

## 1. Legacy Way (C++11 / C++17)
Standard block scope and local object lifetimes.

```cpp
#include <iostream>
#include <string>

int main() {
    {
        std::string msg = "Hello"; // Born here
        std::cout << msg << "\n";  // Output: Hello
    } // msg is DESTROYED here automatically
    
    return 0;
}
```

## 2. Modern Way (C23)
Using **Namespaces** and `auto` for cleaner scope management.

```cpp
#include <iostream>

namespace App { auto version = 1; }

int main() {
    using namespace App;
    std::cout << "Version: " << version << "\n"; // Output: Version: 1
    
    if (auto status = true; status) { // Init-statement scope
        std::cout << "OK\n"; // Output: OK
    }
    // status is not visible here
    return 0;
}
```

# The Logic Bridge
// Logic: When an object goes out of scope, its **Destructor** is called immediately. This ensures that memory, files, or locks are released without manual intervention.
