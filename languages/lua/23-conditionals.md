# 23. Conditionals (Hub)

Conditionals allow a program to make decisions and execute different blocks of code based on certain criteria. Lua uses `if`, `then`, `elseif`, `else`, and `end`.

## Hub Navigation
- [If-Else Logic](./control/if-else.md) - Basic decision making.
- [The Truth Rule](./22-truth-rule.md) - Understanding what evaluates to true/false.

## 1. Legacy Way (Conventional)
Standard `if-else` structure.

```lua
local age = 18

if age >= 18 then
    print("Adult")
else
    print("Minor")
end
-- Output: Adult
```

## 2. Modern Way (Explicit/EmmyLua)
Using EmmyLua for type-safe condition inputs.

```lua
---@type number
local age = 18

if age >= 18 then
    print("Adult")
else
    print("Minor")
end
-- Output: Adult
```

# The Logic Bridge
Lua's conditional syntax is very readable but requires the `then` keyword after the condition and `end` to close the block. Unlike many languages, Lua does not have a native `switch` or `case` statement. Developers use `elseif` chains or table-based dispatch for similar functionality.
