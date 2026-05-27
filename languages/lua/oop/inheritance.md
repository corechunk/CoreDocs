# Inheritance (PRO)

Definition: Creating a parent-child relationship between objects where the child inherits the parent's attributes and methods. In Lua, this is implemented using the `__index` metamethod.

## 1. Conventional Path
Standard single-level inheritance.

```lua
local Animal = { sound = "..." }
function Animal:speak() print(self.sound) end

local Dog = setmetatable({ sound = "Woof" }, { __index = Animal })
Dog:speak() -- Output: Woof
```

## 2. Explicit Path (Class-like Hierarchy)
A robust multi-level inheritance pattern.

```lua
local Base = {}
Base.__index = Base

function Base:new()
    return setmetatable({}, self)
end

local Derived = setmetatable({}, Base)
Derived.__index = Derived

local d = Derived:new()
```

# The Logic Bridge
// Logic: Inheritance in Lua is **Prototypal**, not Class-based. When a key is missing in a child table, the VM looks up the `__index` field in its metatable. If that metatable is another table, the search continues recursively until the key is found or the chain ends.
