# 🔴 Standard: Synchronization Locks [SYSTEMS]

## Definition
When multiple threads access the same memory, a **Race Condition** can occur. **Mutexes** (Mutual Exclusion locks) ensure that only one thread can enter a "Critical Section" of code at a time.

## 1. Legacy Way (C99 / C11 / C17)
Protecting a shared counter using `pthread_mutex_t`.

```c
#include <stdio.h>
#include <pthread.h>

int counter = 0;
pthread_mutex_t lock;

void* inc(void* arg) {
    pthread_mutex_lock(&lock);
    counter++;
    pthread_mutex_unlock(&lock);
    return NULL;
}

int main() {
    pthread_mutex_init(&lock, NULL);
    // (Thread creation would go here)
    printf("Lock Initialized\n"); // Output: Lock Initialized
    pthread_mutex_destroy(&lock);
    return 0;
}
```

## 2. Modern Way (C23)
Identical logic, mirroring the task while using `nullptr` and C11/C23 native atomic hints.

```c
#include <stdio.h>
#include <pthread.h>

int counter = 0;
pthread_mutex_t lock;

void* inc(void* arg) {
    pthread_mutex_lock(&lock);
    counter++;
    pthread_mutex_unlock(&lock);
    return nullptr;
}

int main() {
    pthread_mutex_init(&lock, nullptr);
    // Mirror same task
    printf("Lock Initialized\n"); // Output: Lock Initialized
    pthread_mutex_destroy(&lock);
    return 0;
}
```

# The Logic Bridge
// Logic: A Mutex is an atomic "Gatekeeper." If a thread tries to lock an already-locked mutex, the Kernel suspends that thread until the gate is opened, ensuring memory consistency.
