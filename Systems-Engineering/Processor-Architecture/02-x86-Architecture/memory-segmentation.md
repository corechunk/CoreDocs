# 📑 x86 Memory Segmentation & Paging

## 1. Global Descriptor Table (GDT)
In Protected Mode, segment registers (`CS`, `DS`, `SS`) act as selectors indexing into the Global Descriptor Table (GDT) to enforce base, limit, and privilege permissions.

## 2. Paging Mechanics (CR3 Register)
Modern x86 operating systems bypass legacy segmentation in favor of 4-level or 5-level page tables, loading root page directory base addresses into control register `CR3`.
