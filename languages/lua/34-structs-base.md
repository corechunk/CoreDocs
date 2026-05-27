# 34 - Structs Base (CORE - Hub)

Definition (The Gateway to Procedural Programming): Lua uses **Tables** as the primary tool for data modeling. When a table is used strictly to group values into a single record without adding behavior, it acts as a "Struct."

## Deep-Dive Reference
For modular procedural architecture:
- [Procedural Mechanisms](./procedural/35-procedural-mechanisms.md)

---

## 1. Conventional Path (Table as Record)
Defining data using the constructor and dot-operator.

```lua
local config = {
    port = 80,
    host = "localhost"
}

config.port = 8080 -- Field access via dot
print(config.host .. ":" .. config.port) -- Output: localhost:8080
```

## 2. Explicit Path (EmmyLua Records)
Using types to enforce a rigid, documented struct-like structure.

```lua
---@class Config
---@field port number
---@field host string
local c = { port = 443, host = "127.0.0.1" }

print(c.port) -- Output: 443
```

# The Logic Bridge
// Logic: Tables in Lua are associative arrays. When used as a "Struct," the string keys act as field names. Because Lua's hash table implementation is highly optimized, using a table as a record has near-zero overhead compared to a fixed C struct.
