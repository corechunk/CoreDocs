# 🔴 Standard: GC Cycles & Tuning [SYSTEMS]

## Definition
The Garbage Collector (GC) behavior can be tuned using `setpause` and `setstepmul`. These parameters control how long the GC waits before starting a new cycle and how fast it runs relative to memory allocation.

## 1. Legacy Way / Method A (Default Tuning)
Using the standard multipliers for balanced performance.

```lua
-- Pause: 200% (waits for memory to double before next cycle)
collectgarbage("setpause", 200)

-- Step Multiplier: 200% (GC runs at 2x the speed of allocation)
collectgarbage("setstepmul", 200)

print("GC tuned to default-ish values") -- Output: GC tuned to default-ish values
```

## 2. Modern Way / Method B (Aggressive Tuning)
Manually controlling the collector for memory-constrained or high-performance systems.

```lua
---@param pause number
---@param step_mul number
local function tuneGC(pause, step_mul)
    -- Lower pause = more frequent collections
    collectgarbage("setpause", pause)
    -- Higher step_mul = faster collections
    collectgarbage("setstepmul", step_mul)
end

-- Aggressive collection: start early, run fast
tuneGC(110, 400)

print("GC tuned for aggressive cleanup") -- Output: GC tuned for aggressive cleanup
```

# The Logic Bridge
// Logic: `setpause` controls the "debt" allowed before the collector starts. `setstepmul` controls the "work" done for each byte allocated. High `stepmul` prevents the GC from falling behind, while low `pause` keeps the memory footprint small at the cost of more CPU usage.
