# Dynamic Arrays

## Explanation
Dynamic Arrays (like `ArrayList` in Java or `vector` in C++) are arrays that can resize themselves. When the array is full and a new element is added, it allocates a larger block of memory (usually double the size) and copies existing elements over.

## Common Methods/Actions
- **add(item) / push_back(item)**: Adds an element at the end. Amortized O(1).
- **get(index)**: O(1) access.
- **set(index, item)**: O(1) update.
- **remove(index)**: O(n) removal as elements need to be shifted.
- **size()**: Returns the current number of elements.
- **capacity()**: Returns the total space currently allocated.
