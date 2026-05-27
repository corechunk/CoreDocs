# 15 - Pattern Matching (PRO)

Definition: Lua does not use standard POSIX or PCRE regex. Instead, it has its own lightweight "Pattern Matching" system. Patterns use `%` as an escape character instead of `\`.

## 1. Legacy Way (Conventional Find)
Basic pattern finding and capture.

```lua
local s = "Hello from 2026"
local date = s:match("%d+") -- Find digits

print(date) -- Output: 2026

local name, year = s:match("(%a+)%s+from%s+(%d+)")
print(name) -- Output: Hello
print(year) -- Output: 2026
```

## 2. Modern Way (Explicit Captures & Gsub)
Using sophisticated captures and replacement logic.

```lua
---@type string
local path = "/usr/bin/lua"

-- Capture everything after the last slash
local filename = path:match("([^/]+)$")
print(filename) -- Output: lua

-- Using gsub for transformation
local template = "User: %name%"
local result = template:gsub("%%(%a+)%%", { name = "Corechunk" })
print(result) -- Output: User: Corechunk
```

# The Logic Bridge
Lua patterns are designed to be small and fast, fitting into the minimal Lua VM. While less powerful than full Regex (e.g., no alternation `|`), they are extremely efficient for most parsing tasks. Use `%` for character classes: `%d` (digit), `%a` (alpha), `%s` (space), `%p` (punctuation).
