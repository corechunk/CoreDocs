# 🟢 Passing Mechanisms [CORE]

## Definition
Lua uses two primary mechanisms for passing data to functions: 
1. **Pass-by-Value:** Numbers, booleans, and strings are copied. Modifying them inside a function does not affect the original.
2. **Pass-by-Reference (Sharing):** Tables (and other objects like userdata/threads) are passed by reference. Modifying the table's contents inside a function **will** affect the original table.

## 1. Conventional Path (Implicit Behavior)
Modifying a primitive vs. modifying a table.

```lua
local function modify(val, tbl)
    val = val + 1
    tbl.name = "Modified"
end

local x = 10
local t = { name = "Original" }

modify(x, t)

print(x)      -- Output: 10
print(t.name) -- Output: Modified
```

## 2. Explicit Path (EmmyLua & Typed Reference)
Clarifying the intent with type annotations.

```lua
---@param val number
---@param tbl table
local function modify(val, tbl)
    val = val + 1
    tbl.name = "Modified"
end

local x = 10
---@table t
local t = { name = "Original" }

modify(x, t)

print(x)      -- Output: 10
print(t.name) -- Output: Modified
```

# The Logic Bridge
Lua variables for tables do not store the table itself; they store a **pointer** to the table's memory location. When you pass a table to a function, you are copying the pointer, not the data. Primitives, however, are stored directly in the variable's stack slot and are copied bit-for-bit.
