# 🟢 Associative Collections (Hash Maps) [CORE]

## Definition
Any value in Lua (except `nil` and `NaN`) can be used as a key in a table. When non-integer keys are used, the table acts as a **Hash Map** or **Dictionary**.

## 1. Conventional Path (Dynamic Keys)
Using strings and numbers as keys.

```lua
local inventory = {}
inventory["apples"] = 10
inventory.oranges = 5 -- Syntactic sugar for ["oranges"]

print(inventory["apples"]) -- Output: 10
print(inventory.oranges)   -- Output: 5

for key, val in pairs(inventory) do
    print(key .. ": " .. val)
end
-- Output: apples: 10
-- Output: oranges: 5
```

## 2. Explicit Path (Typed Maps)
Explicitly defining the key-value types using EmmyLua.

```lua
---@type table<string, number>
local inventory = {
    apples = 10,
    oranges = 5
}

print(inventory["apples"]) -- Output: 10
print(inventory.oranges)   -- Output: 5

---@param k string
---@param v number
for k, v in pairs(inventory) do
    print(k .. ": " .. v)
end
-- Output: apples: 10
-- Output: oranges: 5
```

# # The Logic Bridge
Lua tables are split internally into an **Array part** and a **Hash part**. When you use strings or non-contiguous integers as keys, Lua stores them in the Hash part using a specialized hashing algorithm, ensuring $O(1)$ average time complexity for lookups.
