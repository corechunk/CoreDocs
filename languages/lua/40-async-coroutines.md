# 🔵 Milestone 40: Async & Coroutines (Cooperative Multitasking) [PRO]

## Definition
Lua supports **Coroutines** (Collaborative Multithreading). Unlike OS threads, coroutines are managed by the Lua VM and must explicitly `yield` control back to the caller. They are non-preemptive.

## 1. Legacy Way (Conventional Lua 5.1)
Basic coroutine lifecycle: create, resume, yield.

```lua
local co = coroutine.create(function(val)
    for i = 1, 3 do
        print("Co: " .. i + val)
        coroutine.yield()
    end
end)

coroutine.resume(co, 10) -- Output: Co: 11
coroutine.resume(co)     -- Output: Co: 12
coroutine.resume(co)     -- Output: Co: 13
```

## 2. Modern Way (Explicit/EmmyLua Lua 5.4)
Typed coroutine management using `coroutine.wrap` for easier iteration and to-be-closed variables.

```lua
---@param start_val number
---@return fun():number
local function counter_factory(start_val)
    return coroutine.wrap(function()
        local n = start_val
        while true do
            n = n + 1
            coroutine.yield(n)
        end
    end)
end

local next_val = counter_factory(100)

print(next_val()) -- Output: 101
print(next_val()) -- Output: 102
print(next_val()) -- Output: 103
```

# The Logic Bridge
// Logic: `coroutine.create` returns a `thread` object (a coroutine). `coroutine.resume` starts/resumes it.
// Logic: `coroutine.wrap` is "sugar" that returns a function which, when called, resumes the internal coroutine and returns the yielded values.
// Logic: Unlike threads, there is no race condition here because only one coroutine runs at a time. Control is handed over voluntarily.
