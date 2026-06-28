# 🔒 Executable Virtual Memory Pages (mmap & PROT_EXEC)

## 1. Operating System W^X Security (Write XOR Execute)
Modern operating systems enforce strict security boundaries. Memory pages allocated via standard `malloc` are marked Read/Write (`PROT_READ | PROT_WRITE`) but non-executable (`PROT_EXEC` disabled), causing CPU execution panics if jumped to directly.

## 2. Kernel Allocation via mmap()
JIT engines request dynamic executable memory pages directly from the Linux kernel using `mmap()`:

```c
void* code_ram = mmap(NULL, page_size, 
                      PROT_READ | PROT_WRITE | PROT_EXEC, 
                      MAP_ANONYMOUS | MAP_PRIVATE, -1, 0);
```
