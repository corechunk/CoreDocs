# 04 - Tokens & Lexemes (CORE)

Definition: Python's lexer breaks source code into tokens. Unique to Python is the use of indentation as a token (`INDENT`, `DEDENT`).

## 1. Modern Path (3.12+ / Idiomatic)
Implicit line joining in brackets.

```python
items = [
    1,
    2,
    3 # No backslash needed
]
```

## 2. Systems Path (Internals / C-Interop)
Using the `tokenize` module to see the stream.

```python
import tokenize
from io import BytesIO

code = "x = 1"
tokens = tokenize.tokenize(BytesIO(code.encode('utf-8')).readline)
for t in tokens: print(t)
# Logic: Shows NAME, OP, NUMBER, NEWLINE tokens.
```

## 3. Portable Path (Zero-Dependency)
Standard identifier rules.

```python
var_name = 10
_private = True
```

## 4. Strict Path (Type-Hinted)
Manual token boundary verification.

```python
(x := 10) # Walrus operator token
```

# The Logic Bridge
// Logic: Python's parser is a PEG (Parsing Expression Grammar) parser as of 3.9. The lexer handles significant whitespace by keeping a stack of indentation levels, generating `INDENT` tokens when a line starts with more whitespace than the previous, and `DEDENT` when it starts with less.
