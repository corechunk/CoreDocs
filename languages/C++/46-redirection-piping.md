# 🔵 Standard: Redirection & Piping [PRO]

## Definition
Redirecting streams in C++ involves manipulating the **Stream Buffers** (`std::streambuf`).

## 1. Legacy Way (C++11 / C++17)
Redirecting `cout` to a file.

```cpp
#include <iostream>
#include <fstream>

int main() {
    std::ofstream out("log.txt");
    auto old_buf = std::cout.rdbuf(out.rdbuf()); // Swap buffers

    std::cout << "Redirected"; // Writes to log.txt
    
    std::cout.rdbuf(old_buf); // Restore
    std::cout << " Restored\n"; // Output: Restored
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring redirection using modern attributes.

```cpp
#include <iostream>
#include <fstream>

int main() {
    std::ofstream out("log.txt");
    [[maybe_unused]] auto old_buf = std::cout.rdbuf(out.rdbuf());

    std::cout << "Redirected";
    
    std::cout.rdbuf(old_buf);
    std::cout << " Restored\n"; // Output: Restored
    return 0;
}
```

# The Logic Bridge
// Logic: Every stream object (`std::ostream`) delegates the actual byte-writing to a buffer object. Swapping these pointers allows C++ to transparently redirect output to files, strings, or network pipes.
