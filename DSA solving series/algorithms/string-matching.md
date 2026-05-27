# String Matching Algorithms

## Explanation
Algorithms used to find one or more occurrences of a pattern string within a larger text string.

## Algorithms
- **Knuth-Morris-Pratt (KMP)**: Uses a prefix function to avoid redundant comparisons.
- **Rabin-Karp**: Uses hashing to find patterns.
- **Z-Algorithm**: Based on the Z-array, which stores the length of the longest common prefix between the text and a suffix.

## Complexity Analysis
- **KMP**: O(n + m) time, O(m) space.
- **Rabin-Karp**: Average O(n + m) time, Worst O(n * m).
- **Z-Algorithm**: O(n + m) time and space.
