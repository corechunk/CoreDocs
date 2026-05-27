# 🔵 Standard: Advanced OOP [PRO - Hub]

## Definition
Lua achieves Advanced OOP through **Metatables**. By manipulating the `__index` metamethod, we can simulate complex behaviors like Inheritance, Polymorphism, and Encapsulation.

## Deep-Dive Reference
For complex hierarchies and abstractions:
- [Encapsulation](./encapsulation.md) | [Inheritance](./inheritance.md)
- [Polymorphism](./polymorphism.md) | [Abstraction](./abstraction.md)

---

## 1. Conventional Path (Class Simulation)
The most common way to define a class in Lua.

```lua
local User = {}
User.__index = User

function User.new(name)
    local self = setmetatable({}, User)
    self.name = name
    return self
end

function User:greet()
    print("Hello, I am " .. self.name)
end

local u = User.new("Core")
u:greet() -- Output: Hello, I am Core
```

# The Logic Bridge
// Logic: Lua classes are just tables. The `User.new` function acts as a constructor, returning an empty table whose metatable points to `User`. The `:` syntax automatically passes the instance as the first argument (`self`), facilitating object-like behavior.
