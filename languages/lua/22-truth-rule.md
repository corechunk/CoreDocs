# 22. Truth Rule

In Lua, the rule for truthiness is extremely simple: **Only `false` and `nil` are false. Everything else is true.**

## 1. Legacy Way (Conventional)
Testing various values in `if` statements.

```lua
if 0 then
    print("0 is true") -- Output: 0 is true
end

if "" then
    print("Empty string is true") -- Output: Empty string is true
end

if nil then
else
    print("nil is false") -- Output: nil is false
end
```

## 2. Modern Way (Explicit/EmmyLua)
Using explicit boolean checks to avoid confusion for developers coming from C or Python.

```lua
---@type any
local val = 0

-- Explicitly checking against nil/false vs checking numeric value
if val ~= nil then
    print("Value exists (even if 0)") -- Output: Value exists (even if 0)
end

if val == 0 then
    print("Value is exactly zero") -- Output: Value is exactly zero
end
```

# The Logic Bridge
This is a major "gotcha" for many programmers.
- In **C**: `0` is false.
- In **Python**: `0`, `""`, `[]`, `{}` are false.
- In **Lua**: `0` and `""` are **TRUE**.
Only `false` and `nil` will trigger the `else` branch of a conditional. If you need to check if a number is not zero, you must be explicit: `if x ~= 0 then`.
