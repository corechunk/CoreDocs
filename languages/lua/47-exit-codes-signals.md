# 🔴 Standard: Exit Codes & Signals [SYSTEMS]

## Definition
Exit codes communicate the success or failure of a process to the parent OS. Signals are asynchronous notifications sent to a process (e.g., SIGINT, SIGTERM). Lua provides `os.exit` to terminate and `os.execute` or `io.popen` to capture the exit status of child processes.

## 1. Legacy Way / Method A (Simple Exit Status)
The basic numeric exit status commonly used in Lua 5.1.

```lua
-- Simple exit with code 1 (failure)
-- os.exit(1) -- Commented out to prevent process termination during testing

-- Executing a command and getting a basic return (Version dependent)
local status = os.execute("exit 42")
print(status) -- Output: 10752 (On some systems, 5.1 behavior) or 42 (on others)
```

## 2. Modern Way / Method B (Structured Process Termination)
Using Lua 5.2+ structured return values for clear status interpretation.

```lua
---@param cmd string
---@return boolean, string, number
local function runStructured(cmd)
    ---@type boolean|nil, string, number
    local ok, type, code = os.execute(cmd)
    return ok or false, type, code
end

-- Success case
local ok, type, code = runStructured("echo 'Success'") -- Output: Success
print(ok, type, code) -- Output: true exit 0

-- Failure case
local ok, type, code = runStructured("exit 1")
print(ok, type, code) -- Output: false exit 1

-- Signal case (e.g., process killed)
-- Note: Hard to simulate reliably in a snippet, but logic is:
-- if type == "signal" then print("Killed by signal: " .. code) end

-- Closing script with success explicitly
-- os.exit(true, true) -- true = status 0, second true = close Lua state
```

# The Logic Bridge
// Logic: `os.exit` calls the C `exit()` function, which triggers `atexit` handlers and flushes buffers. `os.execute` uses `system()`, and its return value is the raw wait-status from the Kernel, which Lua 5.2+ automatically decodes into a boolean and category string ("exit" or "signal").
