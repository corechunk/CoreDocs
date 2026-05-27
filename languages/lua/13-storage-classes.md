# 13 - Storage Classes (SYSTEMS)

Definition: In Lua, the equivalent of "storage classes" involves understanding **Upvalues** (external local variables captured by a closure) and the **Global Environment** (`_ENV`).

## 1. Legacy Way (Global Manipulation)
Directly using `_G` to access global variables.

```lua
my_global = "World"

function print_global()
    print(_G["my_global"]) -- Output: World
end

print_global()
```

## 2. Modern Way (Upvalues & _ENV)
Using closures to capture state (Upvalues) and `_ENV` for environment isolation.

```lua
-- Upvalue Example
local function create_counter()
    local count = 0 -- Captured as an Upvalue
    return function()
        count = count + 1
        return count
    end
end

local counter = create_counter()
print(counter()) -- Output: 1
print(counter()) -- Output: 2

-- _ENV Isolation (Lua 5.2+)
local function sandbox()
    local _ENV = { print = print, x = 10 } -- Custom environment
    print(x) -- Output: 10
end
sandbox()
```

# The Logic Bridge
Upvalues are how Lua maintains state without globals, forming the basis of functional programming. `_ENV` is a "hidden" upvalue for every chunk; when you access `x`, Lua actually looks for `_ENV.x`. Manipulating `_ENV` allows for powerful sandboxing and module systems.
