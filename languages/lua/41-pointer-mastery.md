# Template: Pointer Mastery (Userdata) [SYSTEMS]

**Goal:** To explain how Lua bridges the gap between its managed memory and C's raw pointers.

---

## 1. The Definition (Mental Model)
Lua is a "Memory Managed" language (Garbage Collected). C is "Manual."
**Userdata** is a special Lua type that allows Lua to store raw C data (like a pointer to a window or a file handle) inside a Lua variable.

- **Full Userdata:** A block of raw memory managed by Lua's GC.
- **Light Userdata:** A raw C pointer (`void*`) managed manually in C.

## 1. Conventional Path (Abstract Usage)
Most Lua users see Userdata when using files.
```lua
local f = io.open("test.txt", "w")
print(type(f)) -- Output: userdata
f:close()
```

## 2. Explicit Path (C-API Perspective)
Though you cannot create raw pointers in pure Lua, we can distinguish them using the `debug` library or C-modules.
```lua
-- Concept: Light Userdata (A raw address)
---@type lightuserdata
local ptr = some_c_function_returning_ptr()

if ptr == nil then
    print("Null Pointer") -- Output: Null Pointer
end
```

# The Logic Bridge
// Logic: Userdata provides a safe "Box" for C pointers, allowing Lua to hold them without trying to interpret them as Lua objects.
