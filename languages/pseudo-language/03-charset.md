# Template: Character Sets (Charset) [SYSTEMS]

**Goal:** To define how the language interprets raw bytes into characters and handles internationalization.

---

## 1. The Definition (Mental Model)
The wiki must start by explaining the "Character Map."
- **What is it?** A Character Set (Charset) is the "Translator" that maps binary numbers (bits) to human-readable symbols like letters, numbers, and emojis.
- **Why?** Computers only know numbers. Without a charset, the number `65` could be a coordinate, a price, or the letter 'A'. The charset gives the byte its "Meaning."

## 2. Requirement: Encoding Support
The wiki must state the language's native relationship with character standards.
- **Standard:** (e.g., ASCII, Extended ASCII, UTF-8, UTF-16).
- **Unicode Support:** Is it modern-native? How does it handle multi-byte characters?
- **Source Encoding:** What format must the source `.c` or `.sh` file be saved in?

## 3. Requirement: Internal Memory Layout
Document how characters are stored in RAM.
- **Byte Size:** Is a `char` exactly 1 byte? Does it support wider types like `wchar_t`?
- **Termination:** Does it use `\0` (null-terminated) or length-prefixing?

## 4. Requirement: The Length Paradox
- **Byte Count vs. Character Count:** Explain if `length("🍎")` returns 1 (one character) or 4 (the number of bytes it takes to store that emoji in UTF-8).

## 5. Documentation Checklist
- [ ] Clear definition of "Charset."
- [ ] Identify the default encoding.
- [ ] List supported escape sequences (e.g., `\uHHHH`).
- [ ] Document behavior for invalid/illegal byte sequences.
