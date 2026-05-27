# 04 - Tokens & Lexemes (CORE)

## Definition (Mental Model)
Tokens are the smallest meaningful units of the Lua language, including Identifiers (names), Literals (values), and Symbols (operators/delimiters). Lexemes are the raw character sequences that represent these tokens. Understanding them is key to writing valid syntax that the LVM can parse.

## 1. Legacy Way (Flexible/Dynamic Tokens)
Standard identifiers and literals in Lua are highly dynamic, with no built-in distinction between mutable and immutable names at the token level.

```lua
# Standard Identifiers and String Literals
var_name = "Dynamic Value"
var_name = 100 -- Type change is allowed
print(var_name) // Output: 100

-- Multi-line string literal (Legacy)
long_text = [[This is 
a multi-line string]]
print(long_text) // Output: This is \n a multi-line string
```

## 2. Modern Way (Explicit/Attributed Tokens)
Lua 5.4 introduced "Attributes" for local variables, allowing tokens to be marked as `<const>` (cannot be reassigned) or `<close>` (automatic resource cleanup).

```lua
---@type number
local PI <const> = 3.14159

-- PI = 3.14 -- ERROR: attempt to assign to const variable 'PI'
print(PI) // Output: 3.14159

---@type string
local user_name <const> = "Admin"
print(user_name) // Output: Admin
```

# The Logic Bridge
Attributes like `<const>` turn a standard "Local Identifier" token into a "Read-Only Local" token, which is enforced by the compiler rather than just by convention.
