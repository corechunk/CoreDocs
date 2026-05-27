# Template: Comments & Metadata [CORE]

**Goal:** To define how to write human-readable notes and machine-readable instructions (metadata) within the source code.

---

## 1. The Definition (Mental Model)
The wiki must start by explaining the concept of "Comments."
- **What is it?** Comments are sections of a source file that are completely ignored by the compiler or interpreter.
- **Why?** They serve two purposes:
    1.  **For Humans:** To explain the reasoning (the "Why") behind complex logic.
    2.  **For Machines:** To provide special instructions (Directives) or generate automated documentation.

## 2. Requirement: Basic Comment Syntax
Document the standard ways to write notes.
- **Single-line:** (e.g., `//` or `--` or `#`).
- **Multi-line / Block:** (e.g., `/* ... */` or `--[[ ... ]]`).

## 3. Requirement: Documentation Strings (Doc-strings)
Explain how the language supports automated documentation tools (like Doxygen, EmmyLua, or Javadoc).
- **Special Prefixes:** (e.g., `///`, `/**`, or `---`).
- **Standard Tags:** (e.g., `@param`, `@return`, `@throws`).

## 4. Requirement: Metadata & Directives
Document how the language provides special "out-of-band" info to the engine.
- **Shebangs:** (e.g., `#!/bin/bash` at the top of the file).
- **Compiler Directives:** (e.g., `#pragma` in C, `#define` macros).
- **Attributes/Annotations:** (e.g., `[[nodiscard]]` in C++ or `@Deprecated` in Java).

## 5. Documentation Checklist
- [ ] List all comment symbols.
- [ ] Identify the syntax for multi-line blocks.
- [ ] Document the specific "Doc-string" standard used by the local LSP.
- [ ] List mandatory directives (like the Shebang for scripts).
