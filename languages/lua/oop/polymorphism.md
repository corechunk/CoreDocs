# Polymorphism (PRO)

Definition: The ability of an object to respond to calls based on its actual type at runtime. Lua achieves this naturally through its dynamic nature and metatable-based method lookups.

## 1. Conventional Path
Duck typing in action.

```lua
local function make_speak(animal)
    animal:speak() -- Works if animal has a speak method
end
```

## 2. Explicit Path (Method Overriding)
Redefining parent methods in the child prototype.

```lua
local Parent = { msg = "Parent" }
function Parent:greet() print(self.msg) end

local Child = setmetatable({ msg = "Child" }, { __index = Parent })
function Child:greet() print("Hello from " .. self.msg) end

Child:greet() -- Output: Hello from Child
```

# The Logic Bridge
// Logic: Since Lua is dynamically typed, polymorphism is implicit. Method calls are resolved at runtime via hash-table lookups (or metatable chains), allowing any table with the correct keys to substitute for another.
