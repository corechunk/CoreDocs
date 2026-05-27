# Nil (Spoke)

Definition: `nil` is a type with a single value, `nil`, whose main property is to be different from any other value. It usually represents the absence of a useful value.

## 1. Legacy Way (Conventional)
Using `nil` to delete table keys or represent uninitialized states.

```lua
local x
print(x) -- Output: nil

local t = { a = 1, b = 2 }
t.a = nil -- Deletes key 'a' from table
print(t.a) -- Output: nil
```

## 2. Modern Way (Explicit)
Type-checking for `nil` and using it in optional types.

```lua
---@type string|nil
local name = nil

if name == nil then
    print("No name provided") -- Output: No name provided
end

-- Explicitly checking type
print(type(name) == "nil") -- Output: true
```

# The Logic Bridge
In Lua, `nil` acts both as a value and a "deleter" when assigned to table fields. Accessing a non-existent variable or table key always returns `nil` rather than throwing an error, which makes `nil` checks the primary guard in Lua programming.
