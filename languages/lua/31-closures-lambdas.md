# 🔵 Closures & Lambdas [PRO]

## Definition
In Lua, all functions are technically "anonymous" lambdas. A **Closure** is created when an inner function refers to variables from its outer scope (upvalues). The inner function "closes over" these variables, keeping them alive even after the outer function has finished executing.

## 1. Conventional Path (Standard Closure)
A simple counter generator.

```lua
local function make_counter()
    local count = 0
    return function()
        count = count + 1
        return count
    end
end

local c1 = make_counter()
print(c1()) -- Output: 1
print(c1()) -- Output: 2
```

## 2. Explicit Path (Typed Lambdas)
Explicitly defining the function signature and the variable types.

```lua
---@return fun():number
local function make_counter()
    ---@type number
    local count = 0
    
    ---@return number
    return function()
        count = count + 1
        return count
    end
end

local c1 = make_counter()
print(c1()) -- Output: 1
print(c1()) -- Output: 2
```

# The Logic Bridge
When a function references an outer local variable, that variable becomes an **Upvalue**. Lua's garbage collector will not reclaim the upvalue as long as any closure that references it is still reachable. This allows for powerful encapsulation and state management without classes.
