# Template: Standard Library [PRO]

**Goal:** To provide a high-signal index of Lua's built-in global environment and standard libraries.

---

## 1. The Definition (Mental Model)
Lua is famous for its minimal footprint. It does not include "everything but the kitchen sink." Instead, it provides a small set of robust libraries that handle the most common tasks.
- **Global Table:** All libraries (except `_G` itself) live in the global namespace.
- **Philosophy:** If you need more (like JSON or regex), you use `LuaRocks`.

## 2. Requirement: The Core Libraries Index
- **`base`:** (e.g., `print`, `type`, `pairs`, `assert`, `require`).
- **`string`:** (e.g., `find`, `match`, `gsub`, `format`).
- **`table`:** (e.g., `insert`, `remove`, `sort`, `concat`).
- **`math`:** (e.g., `sin`, `random`, `floor`, `huge`).
- **`io`:** (e.g., `open`, `read`, `write`, `popen`).
- **`os`:** (e.g., `date`, `time`, `execute`, `exit`).
- **`utf8`:** (e.g., `len`, `char`, `offset`).
- **`coroutine`:** (e.g., `create`, `resume`, `yield`).
- **`debug`:** (e.g., `getmetatable`, `sethook`).

## 1. Conventional Path (Direct Global Access)
```lua
print(math.pi) -- Output: 3.1415926535898
print(os.time()) -- Output: (current timestamp)
```

## 2. Explicit Path (Localizing for Speed)
In Lua, accessing a global is slower than a local. Professional Lua localizes library functions at the top of the file.
```lua
---@type number
local pi <const> = math.pi

---@type function
local floor <const> = math.floor

print(floor(pi)) -- Output: 3
```

# The Logic Bridge
// Logic: Localizing globals into the current scope's register array eliminates a hash-map lookup in `_G`, resulting in a significant performance boost in tight loops.
