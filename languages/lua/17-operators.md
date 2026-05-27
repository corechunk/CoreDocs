# 17. Operators (Hub)

Operators are symbols that tell the interpreter to perform specific mathematical, relational, or logical manipulations. Lua supports arithmetic, relational, logical, bitwise (5.3+), and concatenation operators.

## Hub Navigation
- [Mathematical Operators](./operator/math.md) - Standard arithmetic.
- [Logical Operators](./operator/logical.md) - `and`, `or`, `not` logic.
- [Bitwise Operators](./operator/bitwise.md) - Low-level bit manipulation (Lua 5.3+).
- [Assignment Operators](./operator/assignment.md) - Variable storage and compound logic.

## 1. Legacy Way (Conventional)
In older or simple Lua scripts, operators are used directly with standard variables without type annotations.

```lua
local a = 10
local b = 20
local sum = a + b
local str = "Value: " .. sum

print(str) -- Output: Value: 30
```

## 2. Modern Way (Explicit/EmmyLua)
Modern Lua development uses EmmyLua annotations to ensure type safety and clarity, especially when working with operator-heavy logic.

```lua
---@type number
local a = 10
---@type number
local b = 20

---@type number
local sum = a + b
---@type string
local str = "Value: " .. tostring(sum)

print(str) -- Output: Value: 30
```

# The Logic Bridge
Lua operators are globally consistent. Unlike some languages where `+` might concatenate strings, Lua uses `+` strictly for math (triggering `__add` metamethods) and `..` strictly for string concatenation (triggering `__concat`). This separation prevents accidental type coercion bugs during arithmetic.
