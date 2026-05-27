# 11 - Interpolation (CORE)

Definition: Lua does not have native "f-string" style interpolation. String concatenation is done using the `..` operator. For more complex formatting, `string.format` (similar to C's `printf`) is the standard approach.

## 1. Legacy Way (Concatenation)
Using `..` to join strings and variables.

```lua
local name = "Corechunk"
local version = 5.4

local greeting = "Hello, " .. name .. "! You are using Lua " .. version .. "."
print(greeting) -- Output: Hello, Corechunk! You are using Lua 5.4.
```

## 2. Modern Way (Explicit Formatting)
Using `string.format` for cleaner logic and precise control.

```lua
---@type string
local name = "Corechunk"
---@type number
local version = 5.4

---@type string
local greeting = string.format("Hello, %s! You are using Lua %.1f.", name, version)
print(greeting) -- Output: Hello, Corechunk! You are using Lua 5.4.

-- Custom Interpolation Function (Modern approach)
local function interpolate(str, vars)
    return (str:gsub("($%b{})", function(w)
        return tostring(vars[w:sub(3, -2)] or w)
    end))
end

print(interpolate("Welcome ${name}", {name = name})) -- Output: Welcome Corechunk
```

# The Logic Bridge
While `..` is simple, it can be inefficient for many concatenations (creating many intermediate strings). `string.format` is the professional standard for building complex messages, providing type safety for numbers (integers vs floats) and alignment.
