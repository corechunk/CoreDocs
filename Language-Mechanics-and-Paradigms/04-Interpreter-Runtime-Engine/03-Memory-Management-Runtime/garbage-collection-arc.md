# 🧹 Automatic Reference Counting (ARC) vs. Tracing Garbage Collection

## 1. Automatic Reference Counting (ARC)
Each heap object retains an integer counter tracking active reference pointers. When a counter reaches zero, memory is freed immediately deterministically. (Requires weak references to resolve reference cycles).

## 2. Tracing Mark-and-Sweep Garbage Collection
- **Mark Phase:** Traverses root pointers (stack frames, globals) to mark all reachable active heap objects.
- **Sweep Phase:** Scans heap pools to reclaim memory occupied by un-marked, unreachable objects.
