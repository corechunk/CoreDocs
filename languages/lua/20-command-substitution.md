# 20. Command Substitution (Pro)

Lua does not have a native `$()` syntax like Bash. Instead, it uses `os.execute` for simple execution and `io.popen` for capturing output (command substitution).

## 1. Legacy Way (Conventional)
Using `io.popen` to read the result of a shell command.

```lua
local handle = io.popen("echo Hello from Shell")
local result = handle:read("*a")
handle:close()

print(result) -- Output: Hello from Shell
```

## 2. Modern Way (Explicit/EmmyLua)
Using EmmyLua to handle file handles and clean up properly.

```lua
---@param cmd string
---@return string
local function capture(cmd)
    ---@type file*|nil
    local f = io.popen(cmd)
    if not f then return "" end
    
    ---@type string
    local s = f:read("*a")
    f:close()
    return s:gsub("%s+$", "") -- Trim trailing newline
end

local output = capture("uname -s")
print(output) -- Output: Linux (or your OS)
```

# The Logic Bridge
In shell scripting, `$(cmd)` is built-in. In Lua, you must open a pipe to the process.
- `os.execute(cmd)`: Returns exit status (boolean/string/number depending on Lua version). Good for "fire and forget".
- `io.popen(cmd)`: Returns a file handle to read the process's `stdout`. Good for capturing data.
**Warning:** `io.popen` is not available on all platforms (e.g., some embedded systems) and is potentially dangerous if passed un-sanitized user input.
