# 🟢 Standard: I/O Streams [CORE]

## Definition
I/O (Input/Output) streams in Lua are handled primarily through the `io` library. It supports two models: a "simple" model where a default file handles all operations, and an "explicit" model where file handles are used. `io.write` and `io.read` target standard output and input by default.

## 1. Legacy Way / Conventional Path (The "Auto" Path)
The high-level, global `io` functions for quick scripts.

```lua
-- Writing to stdout
io.write("Enter your name: ") -- Output: Enter your name: 

-- Reading from stdin
local name = io.read() -- User inputs "Alice"

-- Formatting output
io.write(string.format("Hello, %s!\n", name)) -- Output: Hello, Alice!
```

## 2. Modern Way / Explicit Path (MANDATORY)
Using file handles and EmmyLua annotations for strict type safety and clarity.

```lua
---@param prompt string
---@return string|nil
local function promptUser(prompt)
    ---@type file*
    local stdout = io.stdout
    ---@type file*
    local stdin = io.stdin

    stdout:write(prompt) -- Output: Enter your name: 
    
    ---@type string|nil
    local input = stdin:read("*l")
    return input
end

---@type string|nil
local name = promptUser("Enter your name: ")

if name then
    io.stdout:write("Hello, " .. name .. "!\n") -- Output: Hello, Alice!
end
```

# The Logic Bridge
// Logic: The `io` library is a wrapper around the C Standard I/O library (stdio.h). The "Auto" path uses pre-defined global handles (`stdin`, `stdout`, `stderr`), while the "Explicit" path uses Lua's `userdata` to wrap `FILE*` pointers.
