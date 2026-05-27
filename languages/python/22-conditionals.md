# 22 - Conditionals (CORE - Hub)

Definition: Conditionals control the flow of execution based on Boolean logic. Python features standard `if-else` blocks and modern `match-case` for structural pattern matching.

## 1. Modern Path (3.12+ / Idiomatic)
Structural Pattern Matching (The "Pythonic Switch").

```python
status = 404

match status:
    case 200:
        print("OK")
    case 404:
        print("Not Found") # Output: Not Found
    case _:
        print("Unknown")
```

## 2. Systems Path (Internals / C-Interop)
Conditional evaluation and "short-circuiting" internals.

```python
def check():
    print("Checked")
    return True

# Short-circuit: check() is NEVER called
False and check() 
```

## 3. Portable Path (Zero-Dependency)
Standard `if/elif/else` logic.

```python
score = 85
if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
else:
    grade = "F"
print(grade) # Output: B
```

## 4. Strict Path (Type-Hinted)
Exhaustive checks with Enums.

```python
from enum import Enum

class State(Enum):
    ON = 1
    OFF = 0

current: State = State.ON

if current == State.ON:
    print("Active") # Output: Active
```

# The Logic Bridge
// Logic: Python's `match-case` is more than a switch statement; it is a structural pattern matcher that can deconstruct complex objects. At the bytecode level, `if-else` uses `POP_JUMP_IF_FALSE` instructions, while `match` uses a more complex set of lookup instructions designed for fast branching.
