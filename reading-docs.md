# 🏗️ How to Read Documentation (The "Contract" Method)
*Stop reading like a book; read like a Lawyer.*

Professional documentation is not meant to be read cover-to-cover. It is a technical reference meant to be queried for specific "Contractual" guarantees.

### 1. The Signature (Synopsis)
- What does it take (Inputs)?
- What does it return (Outputs)?
- What are the types? (Are they generic? Fixed? Pointers?)

### 2. Side Effects
- Does it modify global state?
- Does it allocate heap memory that YOU must free?
- Does it perform I/O?

### 3. Failure Modes
- What are the error codes?
- Does it throw exceptions?
- What happens with null/invalid input? (Undefined behavior vs. safe crash).

### 4. Complexity
- What are the Time (O) and Space (Ω) guarantees?
- Is it a constant-time lookup or a linear scan?

### 5. Ownership
- If it returns a pointer/resource, who "owns" it?
- Does the library manage the memory, or is it transferred to the caller?

[➔ Back to Official Docs Index](./Necessary-Repos/official-docs-index.md)
