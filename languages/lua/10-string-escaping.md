# 10 - String Escaping (CORE)

Definition: Strings in Lua are sequences of bytes. Lua supports standard C-style escape sequences (like `\n`, `\t`) and allows for long strings using double brackets `[[ ]]`.

## 1. Legacy Way (Standard Escaping)
Using backslashes for special characters and multiline strings.

```lua
local simple = "Hello\nWorld"
local path = "C:\\Users\\Admin"
local long = [[
This is a
multiline string
in Lua.
]]

print(simple) -- Output: Hello
              -- World
print(path)   -- Output: C:\Users\Admin
print(long)   -- Output: This is a
              -- multiline string
              -- in Lua.
```

## 2. Modern Way (Explicit & Unicode)
Using hexadecimal/decimal escapes and Lua 5.3+ UTF-8 support.

```lua
---@type string
local hex_string = "\x48\x65\x6c\x6c\x6f" -- "Hello"
---@type string
local emoji = "\u{1F600}" -- 😀 (Lua 5.3+)

print(hex_string) -- Output: Hello
print(emoji)      -- Output: 😀

-- Literal strings with balanced brackets
local complex = [=[ String with [[brackets]] inside ]=]
print(complex) -- Output: String with [[brackets]] inside
```

# The Logic Bridge
Lua's long brackets `[[ ]]` are literal; they ignore escape sequences, making them ideal for regex or file paths. The `[=[ ]=]` syntax allows for nesting by adding any number of `=` signs, ensuring the string only closes when a matching pair is found.
