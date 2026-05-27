# 16 - Syntactic Automation (SYSTEMS)

Definition: Syntactic automation in Lua is achieved through **Metatables**. A metatable is a regular table that defines the behavior of another table when specific operations (like addition, indexing, or calling) are performed.

## 1. Legacy Way (Basic Metatable)
Manually setting a metatable to provide default values.

```lua
local t = { name = "Corechunk" }
local mt = {
    __index = function(table, key)
        return "Key '" .. key .. "' not found"
    end
}
setmetatable(t, mt)

print(t.name) -- Output: Corechunk
print(t.age)  -- Output: Key 'age' not found
```

## 2. Modern Way (Operator Overloading)
Using metatables for complex behavior and "Class" simulation.

```lua
local Vector = {}
Vector.__index = Vector

function Vector.new(x, y)
    local self = setmetatable({ x = x, y = y }, Vector)
    return self
end

-- Overloading the '+' operator
function Vector.__add(v1, v2)
    return Vector.new(v1.x + v2.x, v1.y + v2.y)
end

function Vector:__tostring()
    return string.format("Vector(%d, %d)", self.x, self.y)
end

local v1 = Vector.new(10, 20)
local v2 = Vector.new(5, 5)
local v3 = v1 + v2

print(v3) -- Output: Vector(15, 25)
```

# The Logic Bridge
Metatables are Lua's "Magic Methods" (like `__init__` in Python). They allow you to define how tables interact with the language's operators. `__index` is the most important field, enabling inheritance and object-oriented patterns by redirecting missed key lookups to another table or function.
