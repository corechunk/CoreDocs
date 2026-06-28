# ☕ Standard C11 Threads API

Introduced in ISO C11 (`threads.h`), standard threads provide a portable thread interface across platforms supporting standard C runtimes, although support is optional (`__STDC_NO_THREADS__`).

---

### 💻 Portable C11 Thread Execution

```c
#include <stdio.h>
#include <threads.h>

// Thread execution handler
int thread_func(void *arg) {
    int val = *(int *)arg;
    printf("C11 Thread running: received %d\n", val);
    return thrd_success;
}

int main() {
    #ifdef __STDC_NO_THREADS__
        printf("C11 Threads are not supported on this platform.\n");
        return 1;
    #endif

    thrd_t thread;
    int data = 42;

    // Create C11 thread
    if (thrd_create(&thread, thread_func, &data) != thrd_success) {
        perror("Failed to create C11 thread");
        return 1;
    }

    // Await thread completion
    int res;
    thrd_join(thread, &res);
    printf("C11 Thread finished with status %d\n", res);

    return 0;
}
```
