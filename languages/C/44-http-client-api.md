# 🔵 Standard: HTTP Client API [PRO]

## Definition
Standard C has no native HTTP support. High-level network tasks are achieved using libraries like **libcurl**, which abstract the raw socket manipulation into a simple "Easy" interface.

## 1. Legacy Way (C99 / C11 / C17)
Standard libcurl setup using the `NULL` macro.

```c
#include <stdio.h>
#include <curl/curl.h>

int main() {
    CURL* curl = curl_easy_init();
    
    if (curl) {
        printf("CURL Ready\n"); // Output: CURL Ready
        curl_easy_cleanup(curl);
    }
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the same task using `nullptr` and `auto`.

```c
#include <stdio.h>
#include <curl/curl.h>

int main() {
    // auto: Cleaner initialization
    auto curl = curl_easy_init();
    
    if (curl != nullptr) {
        printf("CURL Ready\n"); // Output: CURL Ready
        curl_easy_cleanup(curl);
    }
    return 0;
}
```

# The Logic Bridge
// Logic: Libcurl is a wrapper that handles the complex state machines of the HTTP protocol (Headers, Redirects, Cookies) and uses raw sockets underneath to communicate with servers.
