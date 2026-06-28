# ⚛️ Atomic Operations & Lock-Free Programming

Atomic operations guarantee that a read-modify-write memory cycle executes as a single, indivisible step. Other CPU cores cannot see the variable in an intermediate state.

---

### 🧠 Compare-and-Swap (CAS)

The fundamental building block of lock-free data structures is the CAS instruction. It compares the contents of a memory location to a given value and, only if they are equal, modifies the contents of that memory location to a new given value.

---

### 💻 Atomic Operations in C

```c
#include <stdio.h>
#include <stdatomic.h>

int main() {
    // 1. C11 Atomic Variable
    atomic_int counter = 0;

    // Thread-safe atomic increment (requires no mutex locks)
    atomic_fetch_add(&counter, 1);

    // 2. Compare-and-Swap (CAS)
    int expected = 1;
    int desired = 100;

    // atomic_compare_exchange_strong:
    // If counter == expected, set counter = desired and return true.
    // If counter != expected, load current counter value into expected and return false.
    if (atomic_compare_exchange_strong(&counter, &expected, desired)) {
        printf("CAS successful! Counter is now %d\n", atomic_load(&counter));
    } else {
        printf("CAS failed. Expected was updated to current value: %d\n", expected);
    }

    return 0;
}
```
