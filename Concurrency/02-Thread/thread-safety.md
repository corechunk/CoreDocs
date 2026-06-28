# 🔒 Thread Safety & Synchronization

Sharing memory across threads introduces **race conditions** (data corruption due to interleaved access). POSIX provides several synchronization primitives to control access order.

---

### 💻 Synchronization Primitives in C

```c
#include <pthread.h>
#include <semaphore.h>

// 1. Mutex (Mutual Exclusion Lock - Single owner)
pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;
pthread_mutex_lock(&lock);
shared_resource++; // Critical Section
pthread_mutex_unlock(&lock);

// 2. Semaphore (Counting Lock - Multi-owner/Signaling)
sem_t sem;
sem_init(&sem, 0, 1); // Shared-between-threads, initial value 1
sem_wait(&sem);       // Decrements (blocks if 0)
// Critical section...
sem_post(&sem);       // Increments (unlocks blocker)

// 3. Condition Variable (Signaling State Changes)
pthread_cond_t cond = PTHREAD_COND_INITIALIZER;
pthread_mutex_lock(&lock);
while (!ready) {
    pthread_cond_wait(&cond, &lock); // Releases lock, sleeps, re-acquires on wake
}
pthread_mutex_unlock(&lock);

// 4. Barrier (Thread Synchronization Point)
pthread_barrier_t barrier;
pthread_barrier_init(&barrier, NULL, 4); // Sync 4 threads
pthread_barrier_wait(&barrier);          // Blocks until 4 threads call it
```
