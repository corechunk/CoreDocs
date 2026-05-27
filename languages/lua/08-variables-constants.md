# 08 - Variables & Constants (CORE)

Definition: In Lua, variables are containers for values. By default, variables are global unless explicitly declared with `local`. Lua 5.4 introduced attributes for local variables: `<const>` for read-only variables and `<close>` for variables that are automatically closed when they go out of scope.

## 1. Legacy Way (Conventional Lua)
Standard local variable declaration and manual "constant" simulation via naming conventions.

```lua
local user_name = "Corechunk"
local MAX_RETRIES = 5 -- Conventional constant (can still be modified)

user_name = "Gemini"
MAX_RETRIES = 10 -- No error, though logically it shouldn't happen

print(user_name)   -- Output: Gemini
print(MAX_RETRIES) -- Output: 10
```

## 2. Modern Way (Explicit & 5.4+)
Using Lua 5.4 `<const>` attribute and EmmyLua annotations for strict type safety.

```lua
---@type string
local user_name = "Corechunk"

---@type integer
local MAX_RETRIES <const> = 5 -- Language-level enforcement

user_name = "Gemini"
-- MAX_RETRIES = 10 -- Error: attempt to assign to const variable

print(user_name)   -- Output: Gemini
print(MAX_RETRIES) -- Output: 5
```

# The Logic Bridge
The transition from `local` to `local <const>` provides compile-time (or rather, load-time) safety for immutable data. While naming conventions (UPPERCASE) served as a hint in older versions, Lua 5.4 attributes provide actual protection. EmmyLua annotations (`---@type`) bridge the gap by providing static analysis in IDEs (like LuaLS) that Lua's dynamic nature lacks natively.
