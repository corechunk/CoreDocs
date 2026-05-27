# 🔴 Standard: Linking & Delivery [SYSTEMS]

## Definition
Lua can load and link to C libraries dynamically at runtime. This is done via `package.loadlib` or, more commonly, by placing a `.so` (Linux) or `.dll` (Windows) in the `package.cpath`. This allows Lua to call native C functions at full hardware speed, providing the "Logic" while C provides the "Muscle."

## 1. Legacy Way / Method A (Manual loadlib)
Using the low-level `package.loadlib` to manually map a C function to Lua.

```lua
-- Path to the compiled C library
local path = "./mylib.so"
-- "luaopen_mylib" is the entry point function in C
local f, err = package.loadlib(path, "luaopen_mylib")

if f then
    local mylib = f() -- Execute entry point to get the module table
    mylib.fast_function()
else
    print("Link error: " .. err) -- Output: (Error details if .so not found)
end
```

## 2. Modern Way / Method B (Automatic Search & require)
Using the standard `require` mechanism to find and link C modules.

```lua
-- Ensure the cpath includes current directory
package.cpath = "./?.so;" .. package.cpath

---@type table
local mylib = require("mylib") -- Lua looks for mylib.so and calls luaopen_mylib

---@type number
local result = mylib.compute(10, 20)
print("C-Calculated Result: " .. result) -- Output: C-Calculated Result: 30
```

# The Logic Bridge
// Logic: `package.loadlib` uses the OS-level dynamic linker (`dlopen` on POSIX, `LoadLibrary` on Windows). When `require` finds a binary file, it uses `loadlib` internally to find a function named `luaopen_<modname>`, which must exist in the C source to initialize the module and register its functions into the Lua state.
