# Heaps & Priority Queues

## Explanation
A Heap is a special Tree-based data structure that satisfies the heap property: in a Max-Heap, the parent is always greater than or equal to its children; in a Min-Heap, the parent is always less than or equal to its children. A Priority Queue is often implemented using a Heap.

## Variants
- **Binary Heap**: A complete binary tree.
- **Binomial Heap**: A collection of binomial trees.
- **Fibonacci Heap**: Offers better amortized complexity for some operations.

## Common Methods/Actions
- **insert(item)**: Adds an item while maintaining the heap property. O(log n).
- **extractMin() / extractMax()**: Removes and returns the root element. O(log n).
- **peek() / findMin() / findMax()**: Returns the root element without removing it. O(1).
- **heapify()**: Reorders elements to satisfy the heap property. O(n).
- **increaseKey() / decreaseKey()**: Updates the value of an element. O(log n).
