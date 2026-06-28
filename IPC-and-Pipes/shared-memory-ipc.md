# 💾 Shared Memory IPC

Shared Memory is the fastest IPC mechanism available. Rather than routing data through the operating system kernel via system calls, the OS registers a segment of physical RAM directly into the page translation tables of both processes. Once established, both processes access the memory segment using standard pointers, achieving **zero-copy** performance.

---

### 🧠 Virtual Memory Allocation Mappings

```text
  Process A Virtual Memory                           Process B Virtual Memory
+--------------------------+                       +--------------------------+
|  Private Stack/Heap      |                       |  Private Stack/Heap      |
+--------------------------+                       +--------------------------+
|  Shared Memory Segment   | \                   / |  Shared Memory Segment   |
|  (Virtual Address range) |  \                 /  |  (Virtual Address range) |
+--------------------------+   \               /   +--------------------------+
                                v             v
                         +---------------------------+
                         |  Shared Physical Memory   |
                         |  (Raw RAM Segment)        |
                         +---------------------------+
```

---

### 💻 POSIX Shared Memory in C (UNIX)

```c
#include <stdio.h>
#include <sys/mman.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
#include <string.h>

#define SHM_NAME "/sys_shared_mem"
#define SHM_SIZE 4096

int main() {
    // 1. Create a shared memory object descriptor
    int shm_fd = shm_open(SHM_NAME, O_CREAT | O_RDWR, 0666);
    
    // 2. Set size of shared memory object
    ftruncate(shm_fd, SHM_SIZE);

    // 3. Map shared memory descriptor into process address space
    void *ptr = mmap(0, SHM_SIZE, PROT_READ | PROT_WRITE, MAP_SHARED, shm_fd, 0);

    // 4. Write data directly to raw memory address
    strcpy(ptr, "Zero-copy shared memory data payload.");

    printf("Data written to shared memory: %s\n", (char*)ptr);

    // Cleanup mappings
    munmap(ptr, SHM_SIZE);
    close(shm_fd);
    shm_unlink(SHM_NAME); // Mark memory object for destruction
    return 0;
}
```

---

### 💻 Win32 Page File Mapping in C (Windows)

```c
#include <windows.h>
#include <stdio.h>

#define SHM_NAME L"Local\\MyWinSharedMem"
#define SHM_SIZE 4096

int main() {
    // 1. Create file mapping backed by OS page file
    HANDLE hMapFile = CreateFileMappingW(
        INVALID_HANDLE_VALUE, // Backed by page file, not a disk file
        NULL,                 // Default security
        PAGE_READWRITE,       // Read/write access
        0,                    // High-order DWORD size
        SHM_SIZE,             // Low-order DWORD size
        SHM_NAME              // Name of mapping
    );

    // 2. Map view of file into address space
    void *pBuf = MapViewOfFile(
        hMapFile,
        FILE_MAP_ALL_ACCESS,
        0, 0, SHM_SIZE
    );

    // 3. Write data
    CopyMemory(pBuf, "Zero-copy Win32 shared memory.", 30);
    printf("Data written: %s\n", (char*)pBuf);

    // Cleanup
    UnmapViewOfFile(pBuf);
    CloseHandle(hMapFile);
    return 0;
}
```
