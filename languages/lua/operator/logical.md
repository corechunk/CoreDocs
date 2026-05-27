# Logical Operators

Logical operators in Lua include `and`, `or`, and `not`. Unlike many languages, they do not just return boolean values, but return one of their operands.

## 1. Legacy Way (Conventional)
Using logical operators for basic flow control and short-circuiting.

```lua
local a = true
local b = false

print(a and b) -- Output: false
print(a or b)  -- Output: true
print(not a)   -- Output: false

-- Short-circuiting for default values
local name = nil
local displayName = name or "Guest"
print(displayName) -- Output: Guest
```

## 2. Modern Way (Explicit/EmmyLua)
Using EmmyLua to clarify that logical expressions can return non-boolean types.

```lua
---@type boolean
local a = true
---@type boolean
local b = false

print(a and b) -- Output: false
print(a or b)  -- Output: true
print(not a)   -- Output: false

---@type string|nil
local name = nil
---@type string
local displayName = name or "Guest"
print(displayName) -- Output: Guest
```

# The Logic Bridge
Lua logical operators use **short-circuit evaluation**:
- `a and b`: If `a` is false, returns `a`; otherwise returns `b`.
- `a or b`: If `a` is true, returns `a`; otherwise returns `b`.
This allows the common `value = input or default` pattern, where the first non-false/non-nil value is returned.
