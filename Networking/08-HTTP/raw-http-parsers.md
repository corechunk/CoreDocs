# ⚙️ Raw HTTP/1.1 State Machine Buffer Parsers

This guide details constructing zero-copy C/C++ state machine parsers to extract HTTP headers and body payloads from raw TCP stream buffers.

---

## 1. The HTTP Stream Fragmentation Problem

TCP is a continuous stream of bytes without message boundaries. A single `read()` call might return half an HTTP header, or combine multiple HTTP requests in one buffer.

---

## 2. Finite State Machine (FSM) Parsing Strategy

```text
[ STATE_METHOD ] ──> [ STATE_URI ] ──> [ STATE_HEADERS ] ──> [ STATE_BODY ]
```

Parsers step through buffer byte pointers, searching for carriage return and line feed delimiters (`\r\n`) to transition between parsing states, extracting key-value maps safely without buffer overflow vulnerability risks.
