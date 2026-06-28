# ⚡ IDT Gate Configurations

The Interrupt Descriptor Table contains gate descriptors defining the memory segment, address offset, and privilege level required to trigger a handler.

---

### 🧠 Gate Types

*   **Interrupt Gate**: Automatically disables further interrupts on entry by clearing the Interrupt Flag (`IF`) in the flags register, preventing nested interrupts.
*   **Trap Gate**: Leaves the Interrupt Flag unchanged, allowing other interrupts to interrupt the handler.

---

### 💻 IDT Descriptor Structures in C

```c
#include <stdint.h>

// IDT Entry (Gate Descriptor) structure mapping to x86 hardware specifications
struct idt_entry {
    uint16_t base_low;  // The lower 16 bits of the address to jump to
    uint16_t selector;  // Kernel code segment selector (often 0x08)
    uint8_t  always0;   // Reserved byte (must be 0)
    uint8_t  flags;     // Type and attribute flags (defines privilege ring)
    uint16_t base_high; // The upper 16 bits of the address to jump to
} __attribute__((packed));

// Pointer structure loaded using LIDT assembly instruction
struct idt_ptr {
    uint16_t limit;     // Size of the IDT table minus 1
    uint32_t base;      // Start address of the IDT table
} __attribute__((packed));

struct idt_entry idt[256];
struct idt_ptr idtp;

// Register a handler for a specific interrupt vector
void idt_set_gate(uint8_t num, uint32_t base, uint16_t sel, uint8_t flags) {
    idt[num].base_low = (base & 0xFFFF);
    idt[num].base_high = (base >> 16) & 0xFFFF;
    idt[num].selector = sel;
    idt[num].always0 = 0;
    idt[num].flags = flags; // e.g., 0x8E = Present, Ring 0, Interrupt Gate
}
```
