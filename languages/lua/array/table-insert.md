# 🟢 Table Manipulation (Insert/Remove) [SPOKE]

## Definition
The `table` standard library provides functions to treat tables as dynamic arrays. `table.insert` shifts elements to maintain contiguity, while `table.remove` shifts them back to fill gaps.

## 1. Conventional Path (Standard Library)
Using the built-in library for array operations.

```lua
local list = { "A", "C" }

table.insert(list, 2, "B") -- Insert "B" at index 2
print(list[2]) -- Output: B

table.remove(list, 1) -- Remove "A"
print(list[1]) -- Output: B
```

## 2. Explicit Path (Manual Shift/Append)
Performing the same tasks manually to understand the underlying cost.

```lua
local list = { "A", "C" }

-- Manual Insert "B" at index 2 (simulating shift)
list[3] = list[2]
list[2] = "B"
print(list[2]) -- Output: B

-- Manual Remove index 1 (simulating shift)
list[1] = list[2]
list[2] = list[3]
list[3] = nil
print(list[1]) -- Output: B
```

# # The Logic Bridge
`table.insert` and `table.remove` are $O(n)$ operations because they must shift all subsequent elements in the table's array-part to ensure there are no `nil` "holes" that would break the length operator (`#`).
