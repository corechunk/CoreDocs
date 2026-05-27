# Template: HTTP Client API [PRO]

**Goal:** To demonstrate how to perform web requests in Lua using standard libraries or common external modules.

---

## 1. The Definition (Mental Model)
Lua has no native "HTTP" keyword. Web communication requires either a C-module (`LuaSocket`, `Lua-HTTP`) or a system call to a tool like `curl`.

## 1. Legacy Way (The System Wrapper)
The most portable way to fetch data without installing modules.
```lua
local handle = io.popen("curl -s https://api.github.com/zen")
if handle then
    local result = handle:read("*a")
    handle:close()
    print(result) -- Output: (A random Zen quote)
end
```

## 2. Modern Way (LuaSocket / Explicit)
Using the industry-standard `socket.http` module.
```lua
local http = require("socket.http")

---@type string?, integer?, table?, string?
local response, status, headers, status_text = http.request("http://httpbin.org/get")

if status == 200 then
    print("Success") -- Output: Success
end
```

# The Logic Bridge
// Logic: `io.popen` spawns an external OS process, while `require("socket.http")` uses a compiled C-shared library for direct socket communication.
