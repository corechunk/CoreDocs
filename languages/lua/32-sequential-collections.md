# 🟢 Sequential Collections (Arrays) [CORE]

## Definition
Lua does not have a native "Array" type. Instead, it uses **Tables** with contiguous integer keys starting at **1**. This is the standard for all sequential data in Lua (lists, vectors, stacks).

## 1. Conventional Path (Auto-Indexing)
Creating a list and accessing elements.

```lua
local fruits = { "Apple", "Banana", "Cherry" }

print(fruits[1]) -- Output: Apple
print(#fruits)   -- Output: 3

for i = 1, #fruits do
    print(fruits[i])
end
-- Output: Apple
-- Output: Banana
-- Output: Cherry
```

## 2. Explicit Path (Typed Arrays)
Defining the table as an array of a specific type.

```lua
---@type string[]
local fruits = { "Apple", "Banana", "Cherry" }

print(fruits[1]) -- Output: Apple
print(#fruits)   -- Output: 3

---@param index number
for index = 1, #fruits do
    print(fruits[index])
end
-- Output: Apple
-- Output: Banana
-- Output: Cherry
```

# The Logic Bridge
The `#` operator (length) works by performing a binary search for the first integer key that has a `nil` value following it. If your table has "holes" (non-contiguous integer keys), the behavior of `#` becomes undefined and unreliable. Always ensure sequences are contiguous.
