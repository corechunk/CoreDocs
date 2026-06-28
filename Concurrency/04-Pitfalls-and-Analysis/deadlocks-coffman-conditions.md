# 🔒 Deadlocks & Coffman Conditions

A deadlock is a system state where a set of threads are permanently blocked because each thread holds a resource the other thread needs to proceed.

---

### 🧠 The 4 Coffman Conditions

A deadlock state can occur **if and only if** all four conditions are met simultaneously:

1.  **Mutual Exclusion**: At least one resource must be held in a non-shareable mode (only one thread can use it at a time).
2.  **Hold and Wait**: A thread holding allocated resources can request additional resources without relinquishing its current ones.
3.  **No Preemption**: Resources cannot be forcibly taken from a thread; they must be released voluntarily.
4.  **Circular Wait**: A closed chain of threads exists, where each thread holds one or more resources needed by the next thread in the chain.

---

### 💻 Deadlock Prevention via Lock Ordering in C

To prevent circular wait, always acquire locks in a strict, global order.

```c
#include <pthread.h>

pthread_mutex_t lockA = PTHREAD_MUTEX_INITIALIZER;
pthread_mutex_t lockB = PTHREAD_MUTEX_INITIALIZER;

// Thread 1
void *runner1(void *arg) {
    pthread_mutex_lock(&lockA); // Acquire lockA first
    pthread_mutex_lock(&lockB); // Acquire lockB second
    // Critical section
    pthread_mutex_unlock(&lockB);
    pthread_mutex_unlock(&lockA);
    return NULL;
}

// Thread 2 (Deadlock-Free due to identical lock acquisition order)
void *runner2(void *arg) {
    pthread_mutex_lock(&lockA); // ORDER MATTERS: must lock A first, not B
    pthread_mutex_lock(&lockB);
    // Critical section
    pthread_mutex_unlock(&lockB);
    pthread_mutex_unlock(&lockA);
    return NULL;
}
```
