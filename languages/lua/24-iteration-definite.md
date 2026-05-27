# 24. Iteration: Definite

Definite iteration occurs when the number of iterations is known or defined by a collection. Lua uses the `for` loop for this, which comes in two flavors: numeric and generic.

## 1. Legacy Way (Conventional)
Using standard numeric loops and `ipairs`.

```lua
-- Numeric for: start, stop, [step]
for i = 1, 3 do
    print("Count: " .. i)
end
-- Output: Count: 1
-- Output: Count: 2
-- Output: Count: 3

-- Array iteration
local items = {"A", "B", "C"}
for i, v in ipairs(items) do
    print(i, v)
end
-- Output: 1 A
-- Output: 2 B
-- Output: 3 C
```

## 2. Modern Way (Explicit/EmmyLua)
Annotating loops for better IDE support.

```lua
-- Numeric for
for i = 1, 5, 2 do
    print("Step Count: " .. i)
end
-- Output: Step Count: 1
-- Output: Step Count: 3
-- Output: Step Count: 5

---@type string[]
local list = {"apple", "banana"}
for i, name in ipairs(list) do
    print("Item " .. i .. ": " .. name)
end
-- Output: Item 1: apple
-- Output: Item 2: banana
```

# The Logic Bridge
**The Numeric For:** `for var = start, stop, step do`. The `step` is optional (defaults to 1). All three expressions are evaluated once before the loop starts.
**The Generic For (ipairs):** `ipairs` is a stateless iterator designed for **arrays** (sequences). It starts at index 1 and stops at the first `nil` value.
**Important:** Lua indices start at **1**, not 0.
