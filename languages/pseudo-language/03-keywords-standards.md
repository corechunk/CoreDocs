# Template: Keywords & Standards [CORE]

**Goal:** To define the reserved "vocabulary" of the language and track how that vocabulary has expanded through different architectural versions.

---

## 1. The Definition (Mental Model)
The wiki must start by explaining the concept of a "Keyword" to a new student.
- **What is it?** Keywords are reserved words that have a special, hard-coded meaning to the compiler or interpreter.
- **The Rule:** They form the "Grammar" of the language. Because the language "owns" these words, you cannot use them as names for your own variables or functions.

## 2. Requirement: Evolution Snapshot (Minimal)
Showcase language growth using this slik, delta-based format:
`[Standard] -> [Total Count] [Added: word1, word2...]`

```text
C89 -> 32 [auto, break, case, char, const, ...]
C99 -> 37 [Added: inline, restrict, _Bool, _Complex, _Imaginary]
C11 -> 44 [Added: _Alignas, _Alignof, _Atomic, _Generic, ...]
C23 -> 53 [Added: bool, true, false, nullptr, constexpr, ...]
```

## 3. Requirement: Categorized Master List (Latest)
Provide an exhaustive list of **all** current keywords, grouped by their logical role in the system.
- **Control Flow:** (e.g., `if`, `else`, `switch`, `while`, `for`, `return`)
- **Data Types:** (e.g., `int`, `float`, `void`, `struct`, `union`)
- **Type Qualifiers:** (e.g., `const`, `static`, `volatile`, `extern`)
- **Memory/Internal:** (e.g., `sizeof`, `typedef`, `alignas`)

## 4. Special Case: Keywords vs. Built-ins
If the language is a Shell (Bash), the wiki **must** distinguish:
- **Keywords:** Elements of the shell syntax (e.g., `if`, `[[`, `time`).
- **Built-ins:** Commands that live inside the shell binary (e.g., `cd`, `echo`, `alias`).

## 5. Documentation Checklist
- [ ] Clear definition of "Reserved Word."
- [ ] Minimalist evolution timeline with "Added" markers.
- [ ] Exhaustive master list grouped by purpose.
- [ ] Note on whether keywords can be overridden (usually No).
