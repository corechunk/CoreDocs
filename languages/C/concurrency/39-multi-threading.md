# 🔴 Standard: Multi-Threading [SYSTEMS]

## Definition
Multi-threading allows a single process to execute multiple instruction streams concurrently. In C, this is standardized via the **pthreads** (POSIX Threads) library.

## 1. Legacy Way (C99 / C11 / C17)
Standard thread creation and joining using the `NULL` macro.

```c
#include <stdio.h>
#include <pthread.h>

void* task(void* arg) {
    printf("Thread Running\n"); // Output: Thread Running
    return NULL;
}

int main() {
    pthread_t thread;
    pthread_create(&thread, NULL, task, NULL);
    pthread_join(thread, NULL);
    
    printf("Thread Finished\n"); // Output: Thread Finished
    return 0;
}
```

## 2. Modern Way (C23)
Identical pthread workflow, mirroring the task with `nullptr` and modern C23 attributes.

```c
#include <stdio.h>
#include <pthread.h>

void* task(void* arg) {
    printf("Thread Running\n"); // Output: Thread Running
    return nullptr;
}

int main() {
    pthread_t thread;
    // Mirroring same task with modern nullptr
    pthread_create(&thread, nullptr, task, nullptr);
    pthread_join(thread, nullptr);
    
    printf("Thread Finished\n"); // Output: Thread Finished
    return 0;
}
```

# The Logic Bridge
// Logic: Unlike processes, threads share the same address space (Heap, Globals). Each thread gets its own private "Stack" but can read/write the parent's memory, necessitating synchronization locks.
