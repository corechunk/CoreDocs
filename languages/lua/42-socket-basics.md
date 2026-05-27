# Template: Socket Basics [SYSTEMS]

**Goal:** To define the low-level "Listen and Connect" mechanics in Lua.

---

## 1. The Definition (Mental Model)
Sockets are the "Endpoints" of a network connection. In Lua, we use the `LuaSocket` library to interact with the OS's networking stack.

## 1. Conventional Path (Simple Client)
```lua
local socket = require("socket")
local client = socket.tcp()

client:connect("127.0.0.1", 80)
client:send("Hello Server\n")
client:close()
```

## 2. Explicit Path (Timeout & Error Handling)
```lua
local socket = require("socket")

---@type table
local client = assert(socket.tcp())

-- Set a 5-second timeout
client:settimeout(5)

---@type boolean, string
local ok, err = client:connect("127.0.0.1", 80)

if not ok then
    print("Error: " .. err) -- Output: Error: (e.g. connection refused)
end
```

# The Logic Bridge
// Logic: `socket.tcp()` returns a master object that wraps the underlying OS socket file descriptor.
