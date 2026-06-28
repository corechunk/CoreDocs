# 🚪 System Call Register Conventions

Because userspace stacks are isolated from the kernel, system call arguments cannot be passed on the stack. Instead, they are passed directly inside CPU hardware registers.

---

### 🧠 System Call Numbers & Dispatch Table

1.  Each system call is assigned a unique integer identifier (the **Syscall Number**).
2.  The application loads this number into a specific register (e.g. `EAX` on x86, `RAX` on x86_64, or `a7` on RISC-V).
3.  The application loads the parameters into other registers (e.g., `EBX`, `ECX`, `EDX` on x86).
4.  Upon receiving the trap, the kernel's syscall handler reads the number and dispatches the execution to the corresponding function using a **Syscall Dispatch Table** (an array of function pointers).

---

### 💻 Syscall Dispatcher Implementation in C

```c
#include <stdint.h>

#define SYS_fork  1
#define SYS_write 2
#define SYS_exit  3

// Declaring the actual kernel handlers
int sys_fork(void);
int sys_write(int fd, char *buf, int count);
int sys_exit(int status);

// Array of function pointers mapping numbers to kernel handlers
static int (*syscalls[])(void) = {
    [SYS_fork]  = (int (*)(void))sys_fork,
    [SYS_write] = (int (*)(void))sys_write,
    [SYS_exit]  = (int (*)(void))sys_exit,
};

#define SYSCALL_COUNT 4

// The central kernel system call dispatcher (called from assembly trap handler)
void syscall_dispatcher(int syscall_number, int arg1, int arg2, int arg3) {
    if (syscall_number > 0 && syscall_number < SYSCALL_COUNT && syscalls[syscall_number]) {
        // Retrieve parameters and execute target handler
        int result = syscalls[syscall_number](); // Parameters are read from CPU save state
        (void)result;
    }
}
```
