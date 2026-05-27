# Bit Manipulation

## Explanation
Bit manipulation involves performing operations at the bit level. It is often used for optimization and solving specific problems efficiently.

## Common Operators
- **AND (&)**: 1 if both bits are 1.
- **OR (|)**: 1 if at least one bit is 1.
- **XOR (^)**: 1 if bits are different.
- **NOT (~)**: Inverts all bits.
- **Left Shift (<<)**: Multiplies by 2^k.
- **Right Shift (>>)**: Divides by 2^k.

## Common Tricks
- **Check parity**: `n & 1`.
- **Power of 2**: `n > 0 && (n & (n - 1)) == 0`.
- **Count set bits**: Loop `n &= (n - 1)`.

## Complexity Analysis
- **Time Complexity**: O(1) or O(number of bits).
- **Space Complexity**: O(1).
