# ⚠️ Livelock, Starvation & Priority Inversion

While deadlocks block execution completely, other scheduling hazards allow threads to run but fail to make useful progress.

---

### 🧠 Core Concepts

*   **Livelock**: Threads actively change their state in response to each other, but the state changes loop infinitely without completing any work (e.g., two people trying to pass each other in a hallway, stepping side-to-side in unison).
*   **Starvation**: A runnable thread is perpetually denied runtime scheduling slots or lock access because other threads take priority.
*   **Priority Inversion**: A low-priority thread holds a lock needed by a high-priority thread. If a medium-priority thread preempts the low-priority thread, the high-priority thread is indirectly blocked by the medium-priority thread.

```text
Priority: High (T1) > Medium (T2) > Low (T3)

Step 1: T3 acquires lock L.
Step 2: T1 preempts T3 and requests lock L (T1 blocks on lock, yielding to T3).
Step 3: T2 preempts T3 (T2 has no interest in lock L, but runs anyway).
Result: T1 (High) is waiting for T3 (Low), which is blocked by T2 (Medium).
        T1 is indirectly preempted by T2!
```

---

### 🛡️ Mitigation: Priority Inheritance Protocol

To prevent priority inversion, the kernel temporarily boosts the priority of T3 (low) to match T1 (high) while it holds a lock T1 is waiting for. Once T3 releases the lock, its priority returns to normal.

```c
// POSIX mutex configuration for Priority Inheritance
pthread_mutexattr_t attr;
pthread_mutex_t lock;

pthread_mutexattr_init(&attr);
pthread_mutexattr_setprotocol(&attr, PTHREAD_PRIO_INHERIT); // Enable priority inheritance
pthread_mutex_init(&lock, &attr);
```
