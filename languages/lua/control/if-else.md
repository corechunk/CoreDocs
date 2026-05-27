# If-Else Logic

The `if` statement evaluates a condition and, if true, executes a block of code. `elseif` and `else` provide alternative paths.

## 1. Legacy Way (Conventional)
Using `elseif` chains for multiple conditions.

```lua
local score = 85

if score >= 90 then
    print("Grade: A")
elseif score >= 80 then
    print("Grade: B")
else
    print("Grade: C")
end
-- Output: Grade: B
```

## 2. Modern Way (Explicit/EmmyLua)
Adding EmmyLua to ensure the input variable matches expected types.

```lua
---@type number
local score = 85

if score >= 90 then
    print("Grade: A")
elseif score >= 80 then
    print("Grade: B")
else
    print("Grade: C")
end
-- Output: Grade: B
```

# The Logic Bridge
Note the spelling of `elseif` (one word, no space). This is different from `else if` in C++ or Java. Every `if` block must eventually be terminated with an `end`. Lua's lack of braces `{}` makes it essential to indent properly for readability, although the interpreter only cares about the `then` and `end` keywords.
