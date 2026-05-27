# 🔵 Standard: Redirection & Piping [PRO]

## Definition
Redirection and piping in Lua allow scripts to interact with the OS environment. Redirection changes the source or destination of I/O streams, while piping enables reading from or writing to external processes.

## 1. Legacy Way / Method A (Redirection via Global State)
Manually switching the global input/output files.

```lua
-- Redirecting output to a file
local default_out = io.output()
io.output("output.txt")
io.write("Redirection data\n")
io.output():close()
io.output(default_out) -- Restore

-- Piping: Reading from an external command (Manual)
local f = io.popen("ls -l", "r")
if f then
    local content = f:read("*a")
    print(content) -- Output: (List of files)
    f:close()
end
```

## 2. Modern Way / Method B (Explicit Stream Management)
Using explicit handles and protected calls for robust process interaction.

```lua
---@param cmd string
---@return string
local function captureOutput(cmd)
    ---@type file*|nil, string
    local handle, err = io.popen(cmd, "r")
    
    if not handle then
        error("Failed to execute command: " .. err)
    end

    ---@type string
    local result = handle:read("*a")
    handle:close()
    return result
end

-- Explicit Redirection via handle passing
---@type file*|nil
local file_handle = io.open("log.txt", "a")
if file_handle then
    file_handle:write("Secure log entry\n")
    file_handle:close()
end

---@type string
local files = captureOutput("ls -1")
print(files) -- Output: (List of files, one per line)
```

# The Logic Bridge
// Logic: `io.popen` creates a pipe to a new process, allowing the Lua script to capture `stdout` or feed `stdin`. `io.input/output` modify the internal pointers used by the "simple" I/O model, whereas explicit handles (`io.open`) provide thread-safe, isolated stream control.
