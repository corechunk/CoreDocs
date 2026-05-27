# Sliding Window

## Explanation
The Sliding Window pattern is used to perform operations on a specific window size of a linear data structure (like an array or string) as the window "slides" across the structure.

## Variants
- **Fixed Size**: The window size stays the same (e.g., maximum sum of any contiguous subarray of size k).
- **Variable Size**: The window size expands or shrinks based on certain conditions (e.g., smallest subarray with a sum greater than x).

## Complexity Analysis
- **Time Complexity**: O(n) - Each element is visited at most twice (once by the leading edge and once by the trailing edge).
- **Space Complexity**: O(1) or O(k) - Depending on whether extra space is needed to store window data.
