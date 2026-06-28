# 💾 Runtime Stack Frames vs. Dynamic Heap Allocations

## 1. Thread Stack Frames
Primitive values and local variable frames are pushed onto fast thread stack regions, automatically deallocated when execution unwinds past scope boundaries.

## 2. Heap Allocators
Dynamic objects, dynamic strings, arrays, and escaped closure variables are instantiated within dynamic runtime heap memory pools managed by custom allocators (e.g., arena allocators or `malloc`).
