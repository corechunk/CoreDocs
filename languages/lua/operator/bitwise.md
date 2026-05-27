# Bitwise Operators

Bitwise operators perform operations on the bit representations of numbers. Lua 5.3 introduced native operators, whereas previous versions relied on external libraries.

## 1. Legacy Way (Lua 5.1/JIT)
In Lua 5.1, bitwise operations required the `bit` library (standard in LuaJIT).

```lua
local bit = require("bit")
local a = 5 -- 0101
local b = 3 -- 0011

print(bit.band(a, b)) -- Output: 1 (0001)
print(bit.bor(a, b))  -- Output: 7 (0111)
print(bit.bxor(a, b)) -- Output: 6 (0110)
print(bit.lshift(a, 1)) -- Output: 10 (1010)
```

## 2. Modern Way (Lua 5.3+)
Native operators are used directly, similar to C or Python.

```lua
---@type integer
local a = 5 -- 0101
---@type integer
local b = 3 -- 0011

print(a & b)  -- Output: 1 (Bitwise AND)
print(a | b)  -- Output: 7 (Bitwise OR)
print(a ~ b)  -- Output: 6 (Bitwise XOR)
print(a << 1) -- Output: 10 (Left Shift)
print(a >> 1) -- Output: 2 (Right Shift)
print(~a)     -- Output: -6 (Bitwise NOT)
```

# The Logic Bridge
Before Lua 5.3, all numbers were floats, making bitwise logic non-native. The introduction of the integer subtype in Lua 5.3 enabled native, efficient bitwise operators (`&`, `|`, `~`, `<<`, `>>`). When using LuaJIT, the `bit` library remains the standard due to its 5.1 base.
