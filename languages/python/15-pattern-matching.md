# 15 - Pattern Matching (PRO)

Definition: Structural Pattern Matching (`match-case`) allows for deep inspection of data structures.

## 1. Modern Path (3.12+ / Idiomatic)
Matching complex sequences and classes.

```python
data = ["FETCH", 200]

match data:
    case ["FETCH", status] if status < 400:
        print("Success")
    case ["FETCH", _]:
        print("Failed")
# Output: Success
```

## 2. Systems Path (Internals / C-Interop)
Bytecode inspection of the `match` statement.

```python
import dis
def matching(x):
    match x:
        case 1: return "one"

dis.dis(matching) # Logic: Shows MATCH_VALUE and MATCH_CLASS instructions.
```

## 3. Portable Path (Zero-Dependency)
Literal matching.

```python
cmd = "quit"
match cmd:
    case "quit": exit()
```

## 4. Strict Path (Type-Hinted)
Using Enums in pattern matching.

```python
from enum import Enum
class Type(Enum): A = 1

val: Type = Type.A
match val:
    case Type.A: print("A")
```

# The Logic Bridge
// Logic: Python's `match` is more efficient than a chain of `if-isinstance` because the VM uses a specialized decision tree to narrow down the possible branches in fewer instructions.
