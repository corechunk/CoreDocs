# 🏛️ Master Lua Reference (One-Shot)

**Target Standard:** Lua 5.4
**Pedagogical Model:** Mirrored Logic (Conventional vs. Explicit)
**Documentation Standard:** EmmyLua annotations (---@type, ---@param, ---@return)

---

## 🟢 Tier 1: The Foundation [CORE]

### 01. Variables & Constants
Variables in Lua are global by default unless marked `local`. Lua 5.4 introduced `<const>` for immutable variables.

#### 1. Conventional Path (Dynamic)
```lua
name = "Gemini"
age = 25
local score = 100
score = 110 -- Writable
-- Output: score is 110
```

#### 2. Explicit Path (EmmyLua + 5.4 Const)
```lua
---@type string
local name <const> = "Gemini"

---@type integer
local age = 25

---@type number
local score = 100.0
score = 110.5 -- Writable
-- Output: score is 110.5
```

# The Logic Bridge
// Logic: Lua identifies types at runtime; EmmyLua provides static-like safety for LSPs, while `<const>` enforces immutability at the interpreter level.

---

### 02. Data Types (The 8 Basic Types)
Lua is dynamically typed. The `type()` function returns the string name of the type.

#### 1. Conventional Path
```lua
local val = nil
print(type(val)) -- Output: nil

val = 10
print(type(val)) -- Output: number

val = "text"
print(type(val)) -- Output: string

val = {}
print(type(val)) -- Output: table
```

#### 2. Explicit Path (Strict Differentiation)
```lua
---@type nil
local n = nil

---@type integer
local i = 10

---@type number
local f = 10.5

---@type string
local s = "explicit"

---@type table
local t = { key = "value" }

print(type(i), type(f)) -- Output: number number
-- Note: Lua 5.3+ distinguishes integers internally but type() returns "number".
```

# The Logic Bridge
// Logic: All numbers are "number" to the `type()` function, but Lua 5.3+ optimizes integers into a distinct internal subtype (64-bit).

---

### 03. Conditionals (Truthiness)
In Lua, only `false` and `nil` are false. `0` and empty strings `""` are **true**.

#### 1. Conventional Path
```lua
local status = 0

if status then
    print("Zero is True") -- Output: Zero is True
end
```

#### 2. Explicit Path (Boolean Coercion)
```lua
---@type integer
local status = 0

---@type boolean
local is_true = (status ~= nil and status ~= false)

if is_true then
    print("Logic verified") -- Output: Logic verified
end
```

# The Logic Bridge
// Logic: Lua's truth-rule is simpler than C or Python; everything is true except the two "falsey" values.

---

### 04. Function Engine
Functions are first-class values in Lua. They can be stored in variables and passed as arguments.

#### 1. Conventional Path
```lua
function add(a, b)
    return a + b
end

print(add(5, 10)) -- Output: 15
```

#### 2. Explicit Path (EmmyLua Annotated)
```lua
---Adds two numbers together.
---@param a number The first value.
---@param b number The second value.
---@return number result The sum of a and b.
local function add_explicit(a, b)
    return a + b
end

print(add_explicit(5, 10)) -- Output: 15
```

# The Logic Bridge
// Logic: Functions are assigned to local variables to prevent global namespace pollution.

---

### 05. Tables (The Only Collection)
Tables are the only data structure in Lua. They serve as Arrays, Sets, and Maps.

#### 1. Conventional Path (Array)
```lua
local list = {"A", "B", "C"}
print(list[1]) -- Output: A (Lua is 1-indexed!)
```

#### 2. Explicit Path (Generics)
```lua
---@type string[]
local list = {
    [1] = "A",
    [2] = "B",
    [3] = "C"
}
print(list[1]) -- Output: A
```

# The Logic Bridge
// Logic: Lua tables use hashing for keys; when keys are consecutive integers starting at 1, the interpreter optimizes them into a contiguous array in memory.
