# 🧵 POSIX Threads (pthreads)

The POSIX threads specification (`pthread.h`) is the native systems programming multithreading interface on UNIX, Linux, and macOS platforms.

---

### 💻 Native pthread Execution

```c
#include <stdio.h>
#include <pthread.h>
#include <unistd.h>

void *thread_runner(void *arg) {
    int id = *(int *)arg;
    printf("pthread (ID %d) running.\n", id);
    sleep(1);
    printf("pthread (ID %d) exiting.\n", id);
    return NULL;
}

int main() {
    pthread_t thread;
    int id = 101;

    // Create a joinable POSIX thread
    if (pthread_create(&thread, NULL, thread_runner, &id) != 0) {
        perror("Failed to create pthread");
        return 1;
    }

    printf("Parent main thread waiting...\n");
    // Blocks main execution until target thread terminates
    pthread_join(thread, NULL);
    printf("Parent main thread resumed and terminating.\n");

    return 0;
}
```
