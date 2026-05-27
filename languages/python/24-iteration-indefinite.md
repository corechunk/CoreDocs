# 24 - Iteration: Indefinite (CORE)

Definition: Looping until a condition is met using `while`.

## 1. Modern Path (3.12+ / Idiomatic)
While loops with the Walrus operator.

```python
# Read file until empty line
# while (line := file.readline()): ...
```

## 2. Systems Path (Internals / C-Interop)
Infinite loops and process interrupts.

```python
# while True: pass
# Logic: Consumes 100% of a single CPU core (due to GIL).
```

## 3. Portable Path (Zero-Dependency)
Standard conditional loop.

```python
count = 3
while count > 0:
    print(count)
    count -= 1
```

## 4. Strict Path (Type-Hinted)
Looping with typed state variables.

```python
done: bool = False
while not done:
    done = True
```

# The Logic Bridge
// Logic: `while` loops are implemented via the `JUMP_ABSOLUTE` and `POP_JUMP_IF_FALSE` bytecode instructions. The condition is re-evaluated at the start of every cycle.
