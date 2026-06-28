# 🔒 Process-Shared Mutual Exclusion

Because shared memory segments lack built-in synchronization mechanisms, processes accessing shared memory must coordinate reads and writes to prevent race conditions. This is achieved using **process-shared mutexes** (POSIX) or named kernel synchronization objects (Windows).

---

### 💻 POSIX Process-Shared Mutexes in C (UNIX)

We can configure a POSIX mutex to synchronize multiple processes by storing the mutex structure directly inside a shared memory map and setting the `PTHREAD_PROCESS_SHARED` attribute.

```c
#include <stdio.h>
#include <sys/mman.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <pthread.h>
#include <unistd.h>

#define SHM_NAME "/sys_shared_lock_mem"
#define SHM_SIZE 4096

// Shared memory data structure layout
typedef struct {
    pthread_mutex_t lock;
    int shared_counter;
} shared_data_t;

int main() {
    int shm_fd = shm_open(SHM_NAME, O_CREAT | O_RDWR, 0666);
    ftruncate(shm_fd, SHM_SIZE);
    
    shared_data_t *data = (shared_data_t*)mmap(0, SHM_SIZE, PROT_READ | PROT_WRITE, MAP_SHARED, shm_fd, 0);

    // Parent process initializes the process-shared mutex
    pthread_mutexattr_t attr;
    pthread_mutexattr_init(&attr);
    pthread_mutexattr_setpshared(&attr, PTHREAD_PROCESS_SHARED); // Critical: Enable cross-process share
    
    pthread_mutex_init(&data->lock, &attr);
    data->shared_counter = 0;

    pid_t pid = fork();
    if (pid == 0) {
        // Child Process writes to counter safely
        pthread_mutex_lock(&data->lock);
        data->shared_counter += 10;
        printf("Child: counter incremented to %d\n", data->shared_counter);
        pthread_mutex_unlock(&data->lock);
        return 0;
    }

    // Parent Process writes to counter safely
    sleep(1); // Await child to execute
    pthread_mutex_lock(&data->lock);
    data->shared_counter += 5;
    printf("Parent: final counter value is %d\n", data->shared_counter);
    pthread_mutex_unlock(&data->lock);

    // Cleanup resources
    pthread_mutex_destroy(&data->lock);
    pthread_mutexattr_destroy(&attr);
    munmap(data, SHM_SIZE);
    close(shm_fd);
    shm_unlink(SHM_NAME);
    return 0;
}
```

---

### 💻 Win32 Named Mutex Coordination in C (Windows)

Windows provides named synchronization objects that can be opened by name across unrelated processes to synchronize access to shared blocks.

```c
#include <windows.h>
#include <stdio.h>

#define MUTEX_NAME L"Global\\MyProcessMutex"

int main() {
    // Create/Open a named mutex shared globally across process boundaries
    HANDLE hMutex = CreateMutexW(
        NULL,   // Default security
        FALSE,  // Not initially owned
        MUTEX_NAME
    );

    if (hMutex == NULL) {
        printf("CreateMutex failed (%d)\n", GetLastError());
        return 1;
    }

    printf("Waiting to acquire lock...\n");
    // Wait for ownership of the named mutex (blocks until released by other process)
    DWORD dwWaitResult = WaitForSingleObject(hMutex, INFINITE);

    if (dwWaitResult == WAIT_OBJECT_0) {
        printf("Lock acquired! Performing critical section operations...\n");
        Sleep(2000); // Simulate critical section work
        printf("Releasing lock.\n");
        
        ReleaseMutex(hMutex);
    }

    CloseHandle(hMutex);
    return 0;
}
```
