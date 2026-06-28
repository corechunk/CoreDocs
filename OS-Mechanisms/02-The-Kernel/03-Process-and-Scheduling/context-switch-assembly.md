# 🧵 Context Switching Mechanics

A context switch is the process of storing the execution state (CPU registers) of an active thread so it can be resumed later, and loading the saved state of another thread.

---

### 🧠 Register Preservation

During a context switch, the kernel must save all CPU registers into the thread's TCB or onto its kernel stack.
1.  **Caller-Saved Registers** (`EAX`, `ECX`, `EDX` on x86): Automatically pushed onto the stack by the compiler or CPU when an interrupt handler is entered.
2.  **Callee-Saved Registers** (`EBX`, `ESI`, `EDI`, `EBP`, `ESP`): Saved manually by the kernel's context-switch function.

---

### 💻 Context Switch Representation in C

```c
#include <stdint.h>

// Struct representing the saved CPU registers on the kernel stack during context switch
struct context {
    uint32_t edi;
    uint32_t esi;
    uint32_t ebx;
    uint32_t ebp;
    uint32_t eip; // Saved Instruction Pointer (return address)
};

// Thread Control Block structure
typedef struct {
    int pid;
    enum { RUNNING, RUNNABLE, SLEEPING } state;
    struct context *context; // Pointer to saved registers on the thread's stack
    uint32_t *pgdir;         // Pointer to thread's page directory
} tcb_t;

// The context-switch function signature (implemented in assembly)
// Swaps execution from old_context to new_context
extern void swtch(struct context **old_context, struct context *new_context);
```
