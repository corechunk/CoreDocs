# Template: Tokens & Lexemes [CORE]

**Goal:** To define the "Atoms" of the language—the smallest possible units that the compiler or interpreter can understand.

---

## 1. The Definition (Mental Model)
The wiki must start by explaining the "Building Blocks."
- **What is it?** Tokens are the "Words" of the programming language. Just as a sentence is made of words and punctuation, a program is made of Tokens.
- **Lexeme vs. Token:**
    - **Lexeme:** The actual text written (e.g., `total_count`).
    - **Token:** The category of that text (e.g., Identifier).

## 2. Requirement: Identifier Rules
Define how the programmer creates names.
- **Rules:** (e.g., "Must start with a letter", "No symbols allowed except `_`").
- **Case Sensitivity:** Is `MY_VAR` the same as `my_var`?
- **Naming Conventions:** Standard practices (e.g., camelCase vs snake_case).

## 3. Requirement: Literals
Document how hard-coded values are written.
- **Numbers:** Integers (Dec/Hex/Oct), Floats.
- **Strings:** Quote types (`' '` vs `" "`), multi-line support.
- **Booleans/Nulls:** Specific keywords for `true`, `false`, `null`.

## 4. Requirement: Symbols & Punctuators
List the "Grammar" symbols.
- **Grouping:** Usage of `()`, `{}`, `[]`.
- **Delimiters:** Semicolons, commas, dots.

## 5. Documentation Checklist
- [ ] Definition of "Token" vs "Lexeme."
- [ ] List of naming constraints.
- [ ] Identification of whitespace significance (e.g., is it ignored or required?).
- [ ] Suffixes for literals (e.g., `100L`, `1.5f`).
