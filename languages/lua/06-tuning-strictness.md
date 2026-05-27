# 06 - Tuning Strictness (PRO)

## Definition (Mental Model)
Lua is "Global by Default," meaning any variable declared without the `local` keyword is added to the global `_G` table. In large projects, this leads to "Global Pollution" and hard-to-track bugs. Tuning strictness involves enforcing `local` usage and using static analysis to catch undeclared variables.

## 1. Legacy Way (Default Permissiveness)
The conventional way allows silent creation of globals, which can cause unexpected collisions between unrelated modules.

```lua
-- Global by accident
score = 100 

function update_score()
    score = score + 10 -- Modifies global scope
end

update_score()
print(_G.score) // Output: 110
```

## 2. Modern Way (Explicit Scope / Strict.lua)
Professional Lua development uses "Strict Modules" or environment locking to throw errors when an undeclared global is accessed. Coupled with EmmyLua, we get "Compile-time" safety in the editor.

```lua
-- Using _ENV to lock the current scope (Lua 5.2+)
local _ENV <const> = { 
    print = print, 
    math = math,
    ---@type number
    limit = 100 
}

local my_var = 50
print(my_var) // Output: 50
```
-- unintentional_global = 20 -- ERROR: variable is not defined in _ENV
```

# The Logic Bridge
Strictness "tunes" the Lua environment from a "Permissive Search" (checking `_G` for everything) to an "Explicit Map" (only allowing what is predefined in the current `_ENV`).
