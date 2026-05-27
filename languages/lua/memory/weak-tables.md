# 🔴 Standard: Weak Tables [SYSTEMS]

## Definition
Weak tables are tables whose elements are "weak" references. A weak reference is ignored by the garbage collector. If the only reference to an object is a weak reference, the collector will eventually reclaim that object and remove it from the table.

## 1. Legacy Way / Method A (Weak Values)
Creating a cache where values can be garbage collected.

```lua
local cache = {}
setmetatable(cache, { __mode = "v" }) -- "v" means weak values

do
    local obj = { data = "I am temporary" }
    cache["key"] = obj
end

collectgarbage("collect") -- Force collection

if cache["key"] == nil then
    print("Object was collected") -- Output: Object was collected
end
```

## 2. Modern Way / Method B (Weak Keys & Values)
Using explicit metatable configuration and EmmyLua for architectural clarity.

```lua
---@class Registry
---@field items table<object, any>
local Registry = {}

---@return table
function Registry.new()
    ---@type table
    local t = {}
    -- "k" = weak keys, "v" = weak values, "kv" = both
    ---@type table
    local mt = { __mode = "kv" }
    setmetatable(t, mt)
    return t
end

---@type table
local my_registry = Registry.new()

do
    ---@type object
    local key_obj = { id = 1 }
    my_registry[key_obj] = "Meta-data"
end

collectgarbage("collect")

-- Checking if the entry still exists
local count = 0
for k, v in pairs(my_registry) do count = count + 1 end
print("Entries in registry: " .. count) -- Output: Entries in registry: 0
```

# The Logic Bridge
// Logic: In a normal table, the table itself counts as a "strong" reference to its keys and values, preventing GC. Setting `__mode` on the metatable tells the Lua VM to treat these references as "weak," allowing the mark-and-sweep phase to ignore them if they are not reachable via other strong paths.
