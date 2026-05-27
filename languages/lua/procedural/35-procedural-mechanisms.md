# Procedural Mechanisms (PRO - Hub)

Definition: Lua favors **Composition** over complex inheritance. Procedural logic is often organized by grouping related functions into tables (namespaces).

## Deep-Dive Reference
For modularity and performance:
- [Modules & Require](./modules.md)
- [Local-First Optimization](locals.md)

---

## 1. Conventional Path (Functional Namespace)
Grouping functions in a table to simulate a "class" or "module" without `self`.

```lua
local Physics = {}

function Physics.apply_gravity(y, velocity)
    return y + velocity
end

local pos_y = 100
pos_y = Physics.apply_gravity(pos_y, -9.8)
print(pos_y) -- Output: 90.2
```

## 2. Explicit Path (Typed Module Pattern)
Using explicit signatures and local exports for better performance and type safety.

```lua
---@class Physics
local Physics = {}

---@param y number
---@param velocity number
---@return number
Physics.apply_gravity = function(y, velocity)
    return y + velocity
end

---@type number
local pos_y = 100
pos_y = Physics.apply_gravity(pos_y, -9.8)
print(pos_y) -- Output: 90.2
```

# # The Logic Bridge
By storing functions in a table, we create a **Namespace**. This prevents global scope pollution and allows the Lua compiler to optimize function lookups by caching the table's address. Composition is preferred in Lua because it avoids the complexity and performance overhead of metatable-based inheritance.
