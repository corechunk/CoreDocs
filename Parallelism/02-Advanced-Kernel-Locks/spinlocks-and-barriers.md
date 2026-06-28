# 🔄 Spinlocks & Barriers

Operating system lock designs trade off CPU cycles against context-switch latency.

---

### 🧠 Spinlocks vs. Sleeping Mutexes

*   **Spinlocks (Active Locking)**: The thread loops continuously in userspace checking if a lock is available. It consumes $100\%$ of its CPU core slice, but has zero latency when the lock is released. Ideal for low-latency, short-duration critical sections.
*   **Sleeping Mutexes (Passive Locking)**: If the lock is held, the thread relinquishes its CPU slice, and the OS puts it to sleep. It uses $0\%$ CPU while waiting, but incurs context-switch latency when waking up.

---

### 💻 Spinlock Implementation in C

```c
#include <stdatomic.h>

typedef struct {
    atomic_flag dest; // Atomic boolean state
} spinlock_t;

void spin_init(spinlock_t *lock) {
    atomic_flag_clear(&lock->dest);
}

void spin_lock(spinlock_t *lock) {
    // Loop continuously (spin) until lock state is cleared
    // atomic_flag_test_and_set sets the flag and returns its previous value
    while (atomic_flag_test_and_set(&lock->dest));
}

void spin_unlock(spinlock_t *lock) {
    atomic_flag_clear(&lock->dest); // Release lock state
}
```
