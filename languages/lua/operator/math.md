# Mathematical Operators

Mathematical operators perform arithmetic operations on numeric values. Lua supports addition, subtraction, multiplication, division, floor division (5.3+), modulo, and exponentiation.

## 1. Legacy Way (Conventional)
Basic arithmetic without explicit typing or version checks.

```lua
local x = 10
local y = 3

print(x + y)  -- Output: 13
print(x - y)  -- Output: 7
print(x * y)  -- Output: 30
print(x / y)  -- Output: 3.3333333333333
print(x % y)  -- Output: 1
print(x ^ y)  -- Output: 1000
```

## 2. Modern Way (Explicit/EmmyLua)
Using EmmyLua to define precision and explicitly noting the floor division operator (`//`) introduced in Lua 5.3.

```lua
---@type number
local x = 10
---@type number
local y = 3

print(x + y)  -- Output: 13
print(x - y)  -- Output: 7
print(x * y)  -- Output: 30
print(x / y)  -- Output: 3.3333333333333
print(x // y) -- Output: 3 (Floor Division - Lua 5.3+)
print(x % y)  -- Output: 1
print(x ^ y)  -- Output: 1000
```

# The Logic Bridge
Lua treats all numbers as double-precision floats by default (pre-5.3). Lua 5.3 introduced an internal integer subtype. Standard division `/` always returns a float, while `//` performs floor division, returning an integer if both operands are integers.
