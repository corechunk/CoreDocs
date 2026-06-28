# 🧠 Cache Coherency & False Sharing

CPUs cache RAM data in high-speed local caches (L1, L2, L3) structured in **Cache Lines** (typically 64 bytes).

---

### 🧠 MESI Coherency Protocol

To ensure all CPU cores see a consistent view of memory, the hardware monitors cache-line states using the **MESI** protocol:

*   **M (Modified)**: Cache line is valid but dirty (only present in local cache; RAM is out of date).
*   **E (Exclusive)**: Cache line is valid and clean (identical to RAM; not cached by any other core).
*   **S (Shared)**: Cache line is valid, clean, and shared with other CPU core caches.
*   **I (Invalid)**: Cache line has no valid data (must be fetched from L3 or RAM).

---

### 🧠 False Sharing Hazard

False sharing occurs when two CPU cores execute operations on independent variables that reside within the **same cache line**. Whenever Core 1 writes to Var A, the entire cache line is marked as **Invalid** in Core 2's cache, forcing Core 2 to reload Var B from main memory, killing performance.

```text
+-----------------------------------------------------------+
|                      Cache Line (64 Bytes)                |
|  [ Core 1 edits Var A ]  <--->  [ Core 2 edits Var B ]    |
+-----------------------------------------------------------+
       Forces continuous line invalidation & reloading
```

---

### 💻 Mitigating False Sharing in C

Align variables to cache line boundaries (usually 64 bytes) to ensure they reside on separate lines.

```c
#include <threads.h>

// Bad design: Variables are contiguous and share a cache line
struct BadContainer {
    int thread1_counter;
    int thread2_counter; 
};

// Good design: Variables are aligned to prevent false sharing
struct GoodContainer {
    alignas(64) int thread1_counter;
    alignas(64) int thread2_counter;
};
```
