# Modules & Require (PRO)

Definition: Organizing Lua code into reusable units by returning tables from files and loading them with the `require` function.

## 1. Conventional Path
Returning a table of functions.

```lua
-- In math_utils.lua
local M = {}

function M.add(a, b) return a + b end

return M

-- In main.lua
local mu = require("math_utils")
print(mu.add(10, 5)) -- Output: 15
```

## 2. Explicit Path (EmmyLua)
Defining a class-like module with explicit types.

```lua
---@class MathUtils
local M = {}

---@param a number
---@param b number
---@return number
M.add = function(a, b)
    return a + b
end

return M
```

# The Logic Bridge
// Logic: The `require` function searches `package.path`, executes the file, and caches the returned value in `package.loaded`. Subsequent calls to `require` for the same module return the cached table, preventing redundant execution.
