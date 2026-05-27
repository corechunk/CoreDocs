# 03 - Charset (SYSTEMS)

Definition: Python 3 uses Unicode (UTF-8) for all strings by default.

## 1. Modern Path (3.12+ / Idiomatic)
Handling emojis and Unicode identifiers.

```python
🚀 = "Launch"
print(🚀) # Output: Launch
```

## 2. Systems Path (Internals / C-Interop)
Examining the internal memory representation of characters.

```python
import sys
s = "A"
print(sys.getsizeof(s)) # Output: 50 (Header + 1 byte)
# Logic: Python uses different internal structures (ASCII, UCS2, UCS4) 
# depending on the widest character in the string to save memory.
```

## 3. Portable Path (Zero-Dependency)
Encoding and decoding bytes.

```python
data = "Hello".encode("utf-8")
print(data) # Output: b'Hello'
```

## 4. Strict Path (Type-Hinted)
Explicit `str` vs `bytes` typing.

```python
text: str = "Unicode"
raw: bytes = b"\x41\x42"
```

# The Logic Bridge
// Logic: Python strings are immutable sequences of Unicode code points. CPython uses an optimization called "PEP 393" which stores strings in the most compact form possible (1, 2, or 4 bytes per char) based on the contents.
