# 💾 Virtual Page Directories & Address Translation

Operating systems isolate process memory by dividing virtual memory into fixed-size blocks called **Pages** (typically 4KB) and mapping them to physical RAM blocks called **Frames**.

---

### 🧠 Multi-Level Page Tables

Mapping a flat 4GB or 256TB virtual address space requires gigabytes of page table entries. To save RAM, modern CPUs use **Multi-Level Page Tables** (e.g. 2-level on 32-bit, 4-level on 64-bit x86). If a virtual memory region is unused, its sub-level page tables are not allocated in physical RAM.

```text
32-bit Virtual Address (32 bits total):
+---------------------+-------------------+------------------------+
| Directory Index (10)|  Table Index (10) |  Page Offset (12 bits) |
+---------------------+-------------------+------------------------+
         |                     |                      |
         v                     v                      |
  [Page Directory] ----> [Page Table]                 |
                               |                      v
                               +--------------> [Physical Frame]
```

---

### 💻 Page Table Entry (PTE) Flags in C

A Page Table Entry contains the physical address of the target frame, along with metadata flags enforced by the CPU hardware:

```c
// Bit flags inside a x86 Page Table Entry (PTE)
#define PTE_PRESENT  0x001 // Page is loaded in physical RAM
#define PTE_WRITE    0x002 // Page is Read/Write (if cleared, page is Read-Only)
#define PTE_USER     0x004 // User mode applications can access (if cleared, Ring 0 only)
#define PTE_ACCESSED 0x020 // Set by hardware CPU when read/written (useful for GC/Eviction)
#define PTE_DIRTY    0x040 // Set by CPU on write (indicates disk sync is required)

typedef uint32_t pte_t;

// Check if a page is writable
int is_writable(pte_t entry) {
    return (entry & PTE_WRITE) ? 1 : 0;
}
```
