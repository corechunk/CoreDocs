# 10 - String Escaping (CORE)

Definition: Representing special characters in literals.

## 1. Modern Path (3.12+ / Idiomatic)
Raw strings for paths/regex.

```python
path = r"C:\Users\Name" # No escape needed
```

## 2. Systems Path (Internals / C-Interop)
Byte escapes for binary data.

```python
raw = b"\x00\xff"
```

## 3. Portable Path (Zero-Dependency)
Standard escapes.

```python
s = "Line 1\nLine 2"
```

## 4. Strict Path (Type-Hinted)
Unicode escapes.

```python
s: str = "\u2764"
```

# The Logic Bridge
// Logic: The compiler processes escape sequences at load time. Raw strings (`r""`) tell the lexer to treat backslashes as literal characters, which is essential for C-interop paths or Regular Expressions.
