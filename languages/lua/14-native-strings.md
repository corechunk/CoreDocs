# 14 - Native Strings (PRO)

Definition: Lua strings are objects that can be manipulated using the `string` library. Lua also provides "syntactic sugar" that allows calling string methods directly on string literals or variables using the `:` colon operator.

## 1. Legacy Way (Library Calls)
Using the `string` table explicitly.

```lua
local text = "Lua Programming"
local upper = string.upper(text)
local sub = string.sub(text, 1, 3)

print(upper) -- Output: LUA PROGRAMMING
print(sub)   -- Output: Lua
```

## 2. Modern Way (Object-Oriented Style)
Using the `:` operator for cleaner, chainable calls.

```lua
---@type string
local text = "Lua Programming"

print(text:upper())      -- Output: LUA PROGRAMMING
print(text:sub(1, 3))    -- Output: Lua
print(("test"):rep(3))   -- Output: testtesttest (Literal call)

-- EmmyLua completion works better with this style
```

# The Logic Bridge
The `:` operator works because Lua sets a metatable for all strings where the `__index` field points to the `string` table. `text:upper()` is exactly the same as `string.upper(text)`. This style is preferred in modern Lua for readability and consistency with object-oriented patterns.
