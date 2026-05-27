# 🔴 Standard: Memory Management [SYSTEMS]

## Definition
Lua is a garbage-collected language. It uses an incremental mark-and-sweep collector. In Lua 5.4, a generational mode was introduced, providing better performance for programs with many short-lived objects. Unlike C, memory is not manually freed, but understanding the GC (Garbage Collector) is vital for performance and avoiding "leaks" (objects held in global scope unnecessarily).

## 1. Legacy Way / Method A (Incremental Mode)
The default incremental GC behavior found in all Lua versions.

```lua
-- Force a full collection cycle
collectgarbage("collect")

-- Get memory usage in KB
local mem = collectgarbage("count")
print(string.format("Memory: %.2f KB", mem)) -- Output: Memory: (value) KB

-- Stop the GC
collectgarbage("stop")
-- ... manual work ...
collectgarbage("restart")
```

## 2. Modern Way / Method B (Generational Mode - Lua 5.4)
Explicitly enabling the generational collector for modern performance profiles.

```lua
---@type string
local mode = "generational"

-- Switch to generational mode
---@type string
local prev_mode = collectgarbage("generational")

-- Performing a collection in generational mode
collectgarbage("step")

print("GC Mode set to: " .. mode) -- Output: GC Mode set to: generational

-- Explicitly checking memory threshold
if collectgarbage("count") > 1024 then
    collectgarbage("collect")
end
```

# The Logic Bridge
// Logic: Lua's GC uses a tricolor mark-and-sweep algorithm. The "Generational" mode exploits the hypothesis that most objects die young, scanning only "new" objects frequently and "old" objects rarely, which reduces the pause times compared to the "Incremental" mode.

---

## 📂 Spoke Files (Deep Dives)
- [GC Cycles & Tuning](gc-cycles.md): Deep dive into `collectgarbage` parameters.
- [Weak Tables](weak-tables.md): Memory-safe caching and object tracking.
