# 19. Expressions & Statements

In Lua, an **expression** is something that produces a value, while a **statement** is a command that performs an action.

## 1. Legacy Way (Conventional)
Basic mix of statements (assignments, function calls) and expressions (math, logic).

```lua
local x = 10 + 20 -- "10 + 20" is an expression; the whole line is a statement
print(x)          -- Function call statement

if x > 20 then    -- "x > 20" is an expression used in a control statement
    print("Large")
end
```

## 2. Modern Way (Explicit/EmmyLua)
Clearly separating the two with type-safe annotations.

```lua
---@type number
local x = 10 + 20 -- Expression evaluated to 30

---@type boolean
local isLarge = (x > 20) -- Boolean expression

if isLarge then
    print("Large") -- Output: Large
end
```

# The Logic Bridge
Lua is statement-oriented but allows expressions to be used flexibly. One notable feature is that function calls and assignments are statements. Unlike C, you cannot do `if (x = 10)` because assignment is a statement, not an expression, in Lua. This prevents the common "equals vs assignment" bug in conditionals.
