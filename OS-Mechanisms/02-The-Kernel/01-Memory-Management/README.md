# 💾 Kernel Memory Management

The kernel memory manager virtualizes physical RAM, mapping memory blocks to create isolated virtual address spaces for each process.

---

### 🧠 Physical Allocation vs. Virtual Paging

Memory virtualization is split into two operational layers:

1.  **Physical Memory Allocation**: 
    *   Tracks which physical RAM pages are free or allocated.
    *   Uses algorithms like the **Buddy Allocator** (splitting RAM into powers-of-two blocks to prevent fragmentation) or simple **Bitmaps** (where 1 bit represents a 4KB page).
2.  **Virtual Memory Paging**:
    *   Uses the hardware MMU to map a process's virtual addresses to physical RAM pages.
    *   Organized in multi-level **Page Directories** and **Page Tables**.
    *   The CPU uses a hardware cache called the **TLB** (Translation Lookaside Buffer) to cache virtual-to-physical address translations for speed.

---

### 🗺️ Redirection Directory

*   📄 [**`virtual-page-directories.md`**](./virtual-page-directories.md) — Multi-level page tables, virtual address translation, and TLB management.
*   📄 [**`page-replacement-and-swap.md`**](./page-replacement-and-swap.md) — Handling page faults, swap spaces, and Least Recently Used (LRU) eviction algorithms.
