# 🟢 Standard: Error Handling [CORE]

## Definition
Error handling in Lua is primarily done through "protected calls." Instead of `try-catch` blocks, Lua uses `pcall` (protected call) and `xpcall` (extended protected call). `pcall` returns a boolean status and the error message (or return values), while `xpcall` allows for a message handler (stack traceback).

## 1. Legacy Way / Conventional Path (The "Auto" Path)
Basic `pcall` usage for capturing runtime errors.

```lua
local function risky()
    error("Something went wrong!")
end

local status, err = pcall(risky)

if not status then
    print("Caught error: " .. err) -- Output: Caught error: Something went wrong!
else
    print("Success!")
end
```

## 2. Modern Way / Explicit Path (MANDATORY)
Using `xpcall` with explicit traceback handlers and EmmyLua for robust error management.

```lua
---@param err string
---@return string
local function errorHandler(err)
    return debug.traceback("ERROR: " .. err, 2)
end

---@param a number
---@param b number
---@return number
local function divide(a, b)
    if b == 0 then error("Division by zero") end
    return a / b
end

---@type boolean, any
local status, result = xpcall(function() return divide(10, 0) end, errorHandler)

if not status then
    print(result) -- Output: (Traceback showing ERROR: Division by zero)
else
    print("Result: " .. result)
end
```

# The Logic Bridge
// Logic: When an error occurs in Lua, the interpreter performs a "long jump" back to the nearest protected call. `pcall` captures the error after the stack has already been partially unwound, while `xpcall` calls the error handler *before* the stack is unwound, allowing for full traceback retrieval.
