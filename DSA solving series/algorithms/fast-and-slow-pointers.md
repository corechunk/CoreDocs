# Fast & Slow Pointers

## Explanation
Also known as "Hare and Tortoise" algorithm. It uses two pointers moving at different speeds to detect cycles or find specific positions in a linked list or array.

## Common Use Cases
- **Cycle Detection**: If there's a cycle, the fast pointer will eventually catch up to the slow pointer.
- **Finding the Middle**: When the fast pointer reaches the end, the slow pointer is at the middle.

## Complexity Analysis
- **Time Complexity**: O(n) - Linear traversal.
- **Space Complexity**: O(1) - Only two pointers are used.
