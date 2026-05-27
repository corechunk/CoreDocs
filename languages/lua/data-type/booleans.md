# Booleans (Spoke)

Definition: Lua has a simple boolean type with values `true` and `false`. Crucially, in Lua's truth-rule, ONLY `false` and `nil` are considered falsy. Everything else, including `0` and empty strings `""`, is truthy.

## 1. Legacy Way (Conventional)
Using booleans in control flow.

```lua
local is_active = true
local score = 0

if is_active then
    print("Active") -- Output: Active
end

if score then
    print("0 is truthy!") -- Output: 0 is truthy!
end
```

## 2. Modern Way (Explicit)
EmmyLua annotations and logical operations.

```lua
---@type boolean
local is_valid = false
---@type boolean
local has_access = true

print(is_valid and has_access) -- Output: false
print(is_valid or has_access)  -- Output: true
print(not is_valid)           -- Output: true

-- Common pattern: Default values
local input = nil
local value = input or "Default"
print(value) -- Output: Default
```

# The Logic Bridge
Lua's boolean logic is often used for short-circuiting (the `or` default value pattern). Remember that `0` being truthy is a major departure from languages like C or Python, making explicit comparisons (e.g., `if count > 0 then`) vital.
