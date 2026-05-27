# 🏛️ Master Python Reference: The CoreChunk Protocol

**Standard:** Quad-Snippet (Modern, Systems, Portable, Strict).
**Purpose:** High-density, mirrored learning for all CORE milestones.

---

## 🟢 08 - Variables & Constants [CORE]
Definition: Names pointing to heap-allocated `PyObject` structures.

### 1. Modern / Portable Path
```python
user = "Core"
LIMIT = 10 # Conventional constant
```

### 2. Systems / Strict Path
```python
from typing import Final
user_id: int = 101
LIMIT: Final[int] = 10
# print(hex(id(user_id))) # Systems Address
```
// Logic: Variables are pointers; `Final` is a static contract.

---

## 🟢 09 - Data Types [CORE]
Definition: Everything is an object with reference counts.

### 1. Modern / Portable Path
```python
x = 42      # int
y = 3.14    # float
s = "Hi"    # str
```

### 2. Systems / Strict Path
```python
import sys
huge: int = 10**100
# print(sys.getsizeof(huge)) # Arbitrary precision size
```
// Logic: Python types are C-structs; integers scale dynamically.

---

## 🟢 17 - Operators [CORE]
Definition: Syntactic sugar for Dunder method calls.

### 1. Modern / Portable Path
```python
res = 10 // 3 # Floor: 3
is_in = "P" in "Python" # Output: True
```

### 2. Systems / Strict Path
```python
import operator
res: int = operator.floordiv(10, 3)
# res = 10.__floordiv__(3) # Internal C-hook
```
// Logic: Operators trigger dynamic dispatch to object methods.

---

## 🟢 22 - Conditionals [CORE]
Definition: Branching logic including structural matching.

### 1. Modern / Portable Path
```python
status = 200
match status:
    case 200: print("OK")
    case _: print("Err")
```

### 2. Systems / Strict Path
```python
if status == 200:
    pass # Bytecode: POP_JUMP_IF_FALSE
```
// Logic: `match` uses a decision tree for fast multi-branching.

---

## 🟢 23 - Iteration [CORE]
Definition: Collection traversal via the Iterator Protocol.

### 1. Modern / Portable Path
```python
for i in range(3): print(i)
```

### 2. Systems / Strict Path
```python
it = iter([0, 1, 2])
# next(it) # Manual VM iteration
```
// Logic: Loops catch `StopIteration` to terminate cycles.

---

## 🟢 26 - Function Basics [CORE]
Definition: First-class objects executed in stack frames.

### 1. Modern / Portable Path
```python
def greet(name="Guest"):
    return f"Hi {name}"
```

### 2. Systems / Strict Path
```python
def greet(name: str = "Guest") -> str:
    return "Hi " + name
# print(greet.__code__.co_argcount) # Metadata
```
// Logic: Every call creates a `PyFrameObject` on the VM stack.

---

## 🟢 31 - Sequential Collections [CORE]
Definition: Dynamic arrays of object references.

### 1. Modern / Portable Path
```python
items = [1, 2, 3] # list
point = (1, 2)    # tuple
```

### 2. Systems / Strict Path
```python
from typing import List, Tuple
data: List[int] = [1, 2]
# sys.getsizeof(data) # Array growth logic
```
// Logic: Lists are dynamic `PyObject**` arrays; tuples are fixed.

---

## 🟢 32 - Associative Collections [CORE]
Definition: Optimized hash tables with insertion order preservation.

### 1. Modern / Portable Path
```python
map = {"id": 1}
unique = {1, 2, 2} # {1, 2}
```

### 2. Systems / Strict Path
```python
from typing import Dict, Set
db: Dict[str, int] = {"x": 1}
# hash("x") # Bucket placement
```
// Logic: Dicts separate hash indices from value storage for speed.

---

## 🟢 35 - Class Concept [CORE]
Definition: Blueprints for objects using `__dict__` and MRO.

### 1. Modern / Portable Path
```python
class App:
    def __init__(self, n): self.n = n
```

### 2. Systems / Strict Path
```python
class App:
    n: int
    def __init__(self, n: int) -> None:
        self.n = n
# print(App.mro()) # Inheritance chain
```
// Logic: Object attributes are stored in a hidden instance dictionary.

---

# The Logic Bridge
// Logic: Python bridges the gap between high-level expressive code and low-level C implementation. The CPython VM uses reference counting for immediate cleanup and a cycle detector for long-term health, while the Bytecode compiler ensures portability across architectures.
