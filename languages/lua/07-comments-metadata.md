# 07 - Comments & Metadata (CORE)

## Definition (Mental Model)
Comments in Lua serve two purposes: human-readable notes (ignored by the compiler) and machine-readable metadata (used by Language Servers). While standard comments are for "Why," Metadata (EmmyLua) is for "What" (Types, Params, Returns), providing pseudo-static typing to a dynamic language.

## 1. Legacy Way (Plain Text Comments)
Conventional comments use double-hyphens for single lines and bracketed hyphens for blocks, but they provide no information to the IDE or compiler.

```lua
-- This is a single line comment

--[[
    This is a multi-line 
    block comment
]]

local x = 10 -- Variable comment
```

## 2. Modern Way (EmmyLua Metadata)
The modern standard uses triple-hyphens `---` to trigger EmmyLua annotations. This allows the Lua Language Server (Sumneko/LuaLS) to perform type checking, autocompletion, and refactoring.

```lua
---@class Player
---@field name string
---@field score number
local player = { name = "Hero", score = 0 }

--- Calculates the bonus for a player
---@param p Player The player object
---@param multiplier number The bonus multiplier
---@return number The final bonus value
local function get_bonus(p, multiplier)
    return p.score * multiplier
end

print(get_bonus(player, 1.5)) // Output: 0
```

# The Logic Bridge
Metadata (EmmyLua) transforms "Invisible Text" (Standard Comments) into "Visible Logic" (Type Definitions) that the development tools can actually understand and enforce.
