# Assignment Operators

Assignment operators are used to assign values to variables. Lua is notable for its simplicity in this area, lacking the compound assignment operators (like `+=`) found in many other languages.

## 1. Legacy Way (Conventional)
Standard assignment and multiple assignment.

```lua
local x = 10
local y = 20

-- Multiple assignment
x, y = y, x -- Swapping values
print(x, y) -- Output: 20 10

-- Incrementing (No +=)
x = x + 1
print(x) -- Output: 21
```

## 2. Modern Way (Explicit/EmmyLua)
Using EmmyLua to track typed assignments.

```lua
---@type number
local x = 10
---@type number
local y = 20

---@type number, number
x, y = y, x -- Swapping values
print(x, y) -- Output: 20 10

x = x + 1
print(x) -- Output: 21
```

# The Logic Bridge
Lua uses a "simple is better" philosophy for assignment. It does not support `+=`, `-=`, `++`, or `--`. Every modification must be an explicit assignment (`x = x + 1`). This reduces ambiguity in complex expressions. Multiple assignment (`a, b = c, d`) is a powerful feature often used for swapping or returning multiple values from functions.
