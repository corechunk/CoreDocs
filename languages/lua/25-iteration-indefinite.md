# 25. Iteration: Indefinite

Indefinite iteration occurs when the number of repetitions is not known in advance and depends on a condition. Lua provides `while` and `repeat`.

## 1. Legacy Way (Conventional)
Using `while` and `repeat-until` for dynamic conditions.

```lua
local count = 1
while count <= 3 do
    print("While: " .. count)
    count = count + 1
end
-- Output: While: 1
-- Output: While: 2
-- Output: While: 3

local x = 10
repeat
    print("Repeat: " .. x)
    x = x - 5
until x <= 0
-- Output: Repeat: 10
-- Output: Repeat: 5
```

## 2. Modern Way (Explicit/EmmyLua)
Annotating loop variables.

```lua
---@type number
local i = 1
while i <= 2 do
    print("Modern While: " .. i)
    i = i + 1
end
-- Output: Modern While: 1
-- Output: Modern While: 2

---@type number
local j = 10
repeat
    print("Modern Repeat: " .. j)
    j = j - 5
until j < 5
-- Output: Modern Repeat: 10
```

# The Logic Bridge
- **`while` loop:** Checks the condition **before** executing the block. If the condition is false initially, the block never runs.
- **`repeat-until` loop:** Checks the condition **after** executing the block. The block is guaranteed to run at least once.
Note that `repeat` uses `until <condition>`, which is the opposite of a `while <condition>` loop (it stops when the condition becomes true).
