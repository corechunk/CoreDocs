# 💾 Page Faults, Eviction & Swap Memory

When physical RAM is full, the operating system kernel offloads inactive memory pages to disk space (a **Swap Partition** or Swap File) to free up RAM.

---

### 🧠 The Page Fault Lifecycle

If a process attempts to access a virtual address whose Page Table Entry does not have the `PTE_PRESENT` bit set, the CPU pauses execution and triggers a hardware **Page Fault** trap (Interrupt 14 on x86):

```text
  Process accesses address ---> [ PTE Present? ]
                                   /        \
                                 Yes        No
                                 /            \
                    Access granted          [ Page Fault Trap ] ---> Kernel loads page
                                                                     from Swap disk
```

1.  **Fault Trap**: The CPU jumps to the kernel's Page Fault Interrupt Service Routine.
2.  **Allocation/Eviction**: The kernel checks if there is free physical RAM. If not, it runs a **Page Replacement Algorithm** (e.g. Least Recently Used [LRU] or Clock Algorithm) to select an active page, writes its contents to the swap partition on disk, and marks its PTE as not present.
3.  **Swap In**: The kernel reads the requested page from disk into the newly freed physical memory frame, updates the process's page table, and sets `PTE_PRESENT`.
4.  **Resume**: The kernel returns from the interrupt, instructing the CPU to retry the instruction that triggered the page fault.

---

### 💻 Clock Page Replacement Algorithm (Pseudocode)

The Clock (Second Chance) algorithm approximates LRU efficiently without high memory overhead:

```c
typedef struct {
    int page_id;
    int referenced_bit; // Set by CPU hardware on access
} page_frame_t;

#define FRAME_COUNT 1024
page_frame_t frames[FRAME_COUNT];
int hand = 0; // Clock hand index

int find_page_to_evict() {
    while (1) {
        if (frames[hand].referenced_bit == 0) {
            // Found page with no recent accesses! Evict it.
            int evicted = hand;
            hand = (hand + 1) % FRAME_COUNT;
            return evicted;
        }
        // Give the page a second chance (clear bit) and move hand
        frames[hand].referenced_bit = 0;
        hand = (hand + 1) % FRAME_COUNT;
    }
}
```
