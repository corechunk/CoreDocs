# 🔵 Standard: Multi-File Projects [PRO]

## Definition
Lua handles multi-file projects using the `require` function. This function searches for modules in paths defined by `package.path` and `package.cpath`. Modules are typically files that return a table of functions. `require` also ensures that a module is only loaded once by caching it in `package.loaded`.

## 1. Legacy Way / Method A (Implicit Module Loading)
Loading a module and relying on the global environment or simple returns.

```lua
-- In my_module.lua:
-- local M = {}
-- function M.greet() print("Hello!") end
-- return M

-- In main.lua:
local my_module = require("my_module")
my_module.greet() -- Output: Hello!

-- Trying to load again
local same_module = require("my_module") -- Returns cached version
print(my_module == same_module) -- Output: true
```

## 2. Modern Way / Method B (Path-Aware Explicit Loading)
Configuring `package.path` and using EmmyLua for typed module imports.

```lua
-- Explicitly extending the search path
package.path = package.path .. ";./src/?.lua"

---@type table
local utils = require("utils")

---@type string
local version = utils.VERSION or "1.0.0"

print("Utils Version: " .. version) -- Output: Utils Version: 1.0.0

-- Manual unloading for hot-reload scenarios
package.loaded["utils"] = nil
local fresh_utils = require("utils")
```

# The Logic Bridge
// Logic: `require` first checks `package.loaded` to see if the module is already in memory. If not, it iterates through the string templates in `package.path`, replacing `?` with the module name, and uses the first file found. It then executes the file as a function and stores its return value in the cache.
