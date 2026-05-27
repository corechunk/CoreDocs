# 05 - Keywords & Standards (CORE)

## Definition (Mental Model)
Keywords are reserved words that have special meaning to the Lua compiler. Lua is famous for having a very small keyword set (approx. 22). While the core keywords haven't changed much since Lua 5.1, the "Standards" have evolved to include more robust resource management and stricter variable rules.

## 1. Legacy Way (Lua 5.1 / JIT Baseline)
Lua 5.1 is the "Industry Standard" because of LuaJIT. It lacks modern features like bitwise operators, attributes, and the `utf8` library.

```lua
-- Lua 5.1 standard
local function calculate(a, b)
    if a > b then return a else return b end
end
print(calculate(10, 20)) // Output: 20

-- No bitwise operator support natively (requires bit library)
-- print(10 & 2) -- Syntax Error in 5.1
```

## 2. Modern Way (Lua 5.4 Standard)
Lua 5.4 is the "Modern Specialist," introducing native bitwise operators, the generational garbage collector, and variable attributes for safer coding.

```lua
---@param a number
---@param b number
---@return number
local function calculate(a, b)
    -- Native Bitwise Operator (&, |, ~, <<, >>)
    local mask <const> = 0xFF
    return (a & mask) + b
end

print(calculate(10, 20)) // Output: 30
```

# The Logic Bridge
Modern Lua standards (5.3+) upgraded "Reserved Symbols" (like `&`) to perform tasks that previously required external "Reserved Functions" (like `bit.band`).
