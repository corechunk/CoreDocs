# ⚙️ Linux Futex Internals

A **Futex** (Fast Userspace Mutex) is the Linux kernel synchronization primitive that powers high-level locks (`pthread_mutex_t`).

---

### 🧠 Hybrid Lock Architecture

Futexes optimize synchronization by dividing operations into two phases:

1.  **Fast Path (Userspace)**: If no contention exists, the lock is acquired/released in userspace using atomic operations (e.g., CAS) without invoking system calls.
2.  **Slow Path (Kernel-space)**: If contention is detected (lock is already held), the thread invokes the `futex` system call. The kernel suspends the thread, inserts it into the futex wait queue, and schedules another task.

```text
               +-----------------------------+
               | Acquire Lock Request        |
               +-----------------------------+
                              |
                     [ Contended? ]
                      /          \
                    No            Yes
                    /              \
       +------------------+     +-------------------------------+
       | Atomic CAS       |     | syscall(SYS_futex, ..., WAIT) |
       | (Fast Path, $0$) |     | (Slow Path, Kernel Context)   |
       +------------------+     +-------------------------------+
```

---

### 💻 System Call Mechanics

```c
#include <unistd.h>
#include <sys/syscall.h>
#include <linux/futex.h>
#include <sys/time.h>

// Direct syscall wrappers
long futex_wait(int *uaddr, int val) {
    return syscall(SYS_futex, uaddr, FUTEX_WAIT, val, NULL, NULL, 0);
}

long futex_wake(int *uaddr, int val) {
    return syscall(SYS_futex, uaddr, FUTEX_WAKE, val, NULL, NULL, 0);
}
```
