# Special Types (Spoke)

Definition: `userdata` and `thread` are advanced types. `userdata` allows C/C++ data to be stored in Lua, while `thread` represents coroutines (collaborative multithreading).

## 1. Legacy Way (Conventional Coroutines)
Creating and resuming a coroutine (thread type).

```lua
local co = coroutine.create(function()
    print("Inside coroutine")
end)

print(type(co)) -- Output: thread
coroutine.resume(co) -- Output: Inside coroutine
```

## 2. Modern Way (Explicit & Userdata)
Using EmmyLua for coroutine types and conceptualizing Userdata.

```lua
---@type thread
local routine = coroutine.create(function(msg)
    print("Received: " .. msg)
end)

coroutine.resume(routine, "Hello") -- Output: Received: Hello

-- Userdata (usually returned from C libraries like LFS or SDL)
-- ---@type userdata
-- local file = io.stdin -- stdin is a userdata (file handle)
print(type(io.stdin)) -- Output: userdata
```

# The Logic Bridge
`userdata` is the bridge between Lua and the underlying C environment, enabling the extension of Lua with high-performance modules. `thread` is the foundation of Lua's asynchronous-like behavior via coroutines, which are NOT OS threads but managed by the Lua VM.
