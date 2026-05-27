# 🟢 Return Types & Multiple Returns [CORE]

## Definition
Lua supports returning any number of values from a function. Unlike many languages that require wrapping multiple values in a "Tuple" or "Object," Lua's stack natively handles multiple return values, which can be captured into separate variables.

## 1. Conventional Path (Standard Capturing)
Capturing multiple returns into multiple variables.

```lua
local function get_stats()
    local name = "Player1"
    local score = 100
    return name, score
end

local n, s = get_stats()
print(n) -- Output: Player1
print(s) -- Output: 100
```

## 2. Explicit Path (EmmyLua & Typed Capturing)
Explicitly defining the return types and handling the mapping of values.

```lua
---@return string name
---@return number score
local function get_stats()
    local name = "Player1"
    local score = 100
    return name, score
end

---@type string, number
local n, s = get_stats()
print(n) -- Output: Player1
print(s) -- Output: 100
```

# The Logic Bridge
Lua uses its internal data stack to push multiple values before returning to the caller. If more variables are provided than values returned, the extras become `nil`. If fewer variables are provided, the extra values are silently discarded.
