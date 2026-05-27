# 🟢 Function Basics [CORE]

## Definition
Functions in Lua are "first-class values," meaning they are treated like any other data type (strings, numbers, tables). They can be stored in variables, passed as arguments, and returned from other functions.

## 1. Conventional Path (High-Level)
The standard way to define functions in Lua using syntactic sugar.

```lua
-- Standard global function
function greet(name)
    return "Hello, " .. name
end

-- Standard local function
local function add(a, b)
    return a + b
end

print(greet("Lua")) -- Output: Hello, Lua
print(add(10, 5))    -- Output: 15
```

## 2. Explicit Path (The "Manual" Way)
Showing the underlying reality: functions are just anonymous values assigned to variables. This uses EmmyLua annotations for explicit typing.

```lua
---@param name string
---@return string
local greet = function(name)
    return "Hello, " .. name
end

---@param a number
---@param b number
---@return number
local add = function(a, b)
    return a + b
end

print(greet("Lua")) -- Output: Hello, Lua
print(add(10, 5))    -- Output: 15
```

# The Logic Bridge
The `local function name()` syntax is a compiler-level shortcut for `local name; name = function()`. In Lua, functions are truly anonymous; "naming" them is just an assignment to a variable.
