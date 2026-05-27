# Numbers (Spoke)

Definition: Lua 5.2 and earlier treated all numbers as double-precision floating-point. Lua 5.3+ introduced a distinction between "integers" (usually 64-bit) and "floats" (64-bit doubles), though they both fall under the `number` type.

## 1. Legacy Way (Pre-5.3)
All numbers are doubles. Division always results in a float.

```lua
local a = 10
local b = 3

print(type(a)) -- Output: number
print(a / b)   -- Output: 3.3333333333333
print(10 / 2)  -- Output: 5.0 (Float even if whole)
```

## 2. Modern Way (Lua 5.3+ Explicit)
Explicit integer vs float handling and floor division `//`.

```lua
---@type integer
local a = 10
---@type integer
local b = 3

print(math.type(a)) -- Output: integer
print(a / b)        -- Output: 3.3333333333333 (Float result)
print(a // b)       -- Output: 3 (Integer floor division)
print(10 // 2)      -- Output: 5 (Integer result)

local hex = 0xFF
local binary = 0b1010 -- Lua 5.4+ binary literal
print(hex)    -- Output: 255
print(binary) -- Output: 10
```

# The Logic Bridge
The introduction of integers in 5.3 solved precision issues for large IDs and bitwise operations. Use `math.type()` to distinguish them at runtime. Floor division `//` is the standard for integer math, while `/` always forces a float promotion.
