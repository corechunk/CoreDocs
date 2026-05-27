# 🟢 Recursion & Tail Calls [CORE]

## Definition
Recursion occurs when a function calls itself. Lua features **Tail-Call Optimization (TCO)**: if a function's final action is to return the result of another function (or itself), Lua performs a "jump" instead of a "call," reusing the current stack frame. This prevents stack overflow for deep or infinite recursion.

## 1. Conventional Path (Standard Recursion)
A standard recursive countdown. This consumes a new stack frame for every call.

```lua
local function countdown(n)
    if n <= 0 then 
        return "Done" 
    end
    print(n)
    return countdown(n - 1)
end

print(countdown(3)) 
-- Output: 3
-- Output: 2
-- Output: 1
-- Output: Done
```

## 2. Explicit Path (Optimized Tail-Call)
The same logic, but ensuring the call is in the "tail position." In Lua, `return f(x)` is a tail call. `return 1 + f(x)` is NOT.

```lua
---@param n number
---@return string
local function countdown_tco(n)
    if n <= 0 then 
        return "Done" 
    end
    print(n)
    -- This is a 'proper tail call'
    return countdown_tco(n - 1)
end

print(countdown_tco(3))
-- Output: 3
-- Output: 2
-- Output: 1
-- Output: Done
```

# The Logic Bridge
Tail-Call Optimization works because the interpreter realizes that the current function has nothing left to do after the call returns. It simply clears the current local variables and jumps to the start of the called function, essentially turning recursion into a `goto` loop at the machine level.
