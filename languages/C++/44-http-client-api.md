# 🔵 Standard: HTTP Client API [PRO]

## Definition
C++ HTTP interaction via high-level libraries like **CPR** (C++ Requests) or raw `libcurl`.

## 1. Legacy Way (C++11 / C++17)
Using raw `libcurl`.

```cpp
#include <iostream>
#include <curl/curl.h>

int main() {
    CURL* curl = curl_easy_init();
    if (curl) {
        std::cout << "CURL Init\n"; // Output: CURL Init
        curl_easy_cleanup(curl);
    }
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring same task with `nullptr` and `auto`.

```cpp
#include <iostream>
#include <curl/curl.h>

int main() {
    auto curl = curl_easy_init();
    if (curl != nullptr) {
        std::cout << "CURL Init\n"; // Output: CURL Init
        curl_easy_cleanup(curl);
    }
    return 0;
}
```

# The Logic Bridge
// Logic: High-level libraries wrap the raw Socket API and protocol state machines (HTTP/HTTPS), managing headers and body buffers automatically.
