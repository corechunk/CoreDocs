# 🔵 Standard: Build Tools [PRO]

## Definition
LuaRocks is the standard package manager and build system for Lua. It allows you to install modules (rocks) from a central repository and manage project-specific dependencies via a "rockspec" file. Unlike compiled languages, "building" in Lua often refers to dependency resolution and deployment of scripts.

## 1. Legacy Way / Method A (Global Installation)
Installing modules globally for use by the system's Lua interpreter.

```bash
# Installing a rock globally
luarocks install luasocket

# List installed rocks
luarocks list
```

```lua
-- Using the installed rock
local socket = require("socket")
print(socket._VERSION) -- Output: LuaSocket 3.0-rc1
```

## 2. Modern Way / Method B (Local Tree & Rockspecs)
Managing project dependencies in a local tree and defining them in a `.rockspec` file.

```bash
# Installing dependencies into a local 'lua_modules' folder
luarocks install luasocket --tree lua_modules

# Initializing a project with a rockspec
# luarocks init
```

```lua
-- Configuring the path to include local modules
package.path = "./lua_modules/share/lua/5.4/?.lua;" .. package.path
package.cpath = "./lua_modules/lib/lua/5.4/?.so;" .. package.cpath

---@type table
local socket = require("socket")
print("Local Socket Loaded") -- Output: Local Socket Loaded
```

# The Logic Bridge
// Logic: LuaRocks automates the fetching, compiling (for C modules), and path-placement of Lua libraries. By using `--tree`, developers can avoid version conflicts in the global environment, effectively creating a "virtual environment" for Lua projects similar to Python's `venv` or Node's `node_modules`.
