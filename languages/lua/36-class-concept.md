# 36 - Class Concept (CORE - Hub)

Definition (The Gateway to Object-Oriented Programming): Since Lua has no native `class` keyword, the "Class Concept" is achieved by joining **Data** (Table fields) and **Behavior** (Functions) using the `:` syntax. This binding allows for the simulation of objects and methods.

## Deep-Dive Reference
For complex hierarchies and pillars:
- [Advanced OOP](./oop/37-advanced-oop.md)

---

## 1. Conventional Path (Method Binding)
Using the `:` syntax to automatically pass the `self` pointer.

```lua
local Counter = { value = 0 }

function Counter:increment()
    self.value = self.value + 1
end

Counter:increment()
print(Counter.value) -- Output: 1
```

## 2. Explicit Path (Manual Pointer Passing)
Showing the raw procedural reality behind the syntactic sugar.

```lua
local Entity = { health = 100 }

-- Procedural function acting as a method
Entity.heal = function(self, amount)
    self.health = self.health + amount
end

-- Explicitly passing the object pointer
Entity.heal(Entity, 50)
print(Entity.health) -- Output: 150
```

# The Logic Bridge
// Logic: The `:` operator is "Syntactic Sugar." Calling `obj:method()` is identical to `obj.method(obj)`. This makes the instance pointer explicit at the C-layer of the interpreter, enabling object-like behavior in a purely procedural language.
