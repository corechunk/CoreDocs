# 05 - Keywords & Standards (CORE)

Definition: Keywords are reserved words like `if`, `while`, `match`. Standards evolve via PEPs (Python Enhancement Proposals).

## 1. Modern Path (3.12+ / Idiomatic)
Modern keywords like `match`, `case`, `async`.

```python
async def task(): pass
```

## 2. Systems Path (Internals / C-Interop)
Listing keywords via the `keyword` module.

```python
import keyword
print(keyword.kwlist)
```

## 3. Portable Path (Zero-Dependency)
Basic keywords.

```python
def check():
    if True: return
```

## 4. Strict Path (Type-Hinted)
Soft keywords (like `type` in 3.12).

```python
type Alias = int # 3.12 Type Alias keyword
```

# The Logic Bridge
// Logic: Python differentiates between hard keywords (always reserved) and soft keywords (context-dependent, e.g., `match`). This prevents breaking legacy code when new features are added.
