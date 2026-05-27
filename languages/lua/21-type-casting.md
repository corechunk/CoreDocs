# 21. Type Casting

Type casting in Lua is mostly handled by the built-in functions `tonumber()` and `tostring()`. Lua also performs some automatic coercion.

## 1. Legacy Way (Conventional)
Relying on automatic coercion and simple function calls.

```lua
local val = "100"
local num = tonumber(val) + 50
print(num) -- Output: 150

local str = tostring(123) .. " is a number"
print(str) -- Output: 123 is a number

-- Coercion (Avoid if possible)
print("10" + 20) -- Output: 30
```

## 2. Modern Way (Explicit/EmmyLua)
Explicitly casting and verifying types using EmmyLua.

```lua
---@type string
local input = "42"

---@type number|nil
local num = tonumber(input)

if num then
    print(num + 8) -- Output: 50
end

---@type number
local count = 10
---@type string
local msg = tostring(count) .. " items found"
print(msg) -- Output: 10 items found
```

# The Logic Bridge
Lua is dynamically typed but will attempt to coerce strings to numbers during arithmetic (e.g., `"10" + 20`). However, it will **not** coerce numbers to strings during concatenation automatically in all cases (though `..` usually does).
**Best Practice:** Always use `tonumber()` and `tostring()` to be explicit. `tonumber()` returns `nil` if the string isn't a valid number, which is a perfect safety check.
