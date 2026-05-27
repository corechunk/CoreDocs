# 🟢 Standard: Foundational Logic [CORE]

**Purpose:** To teach the absolute basics while building a systems-level mental model. Every topic tagged as **[CORE]** in a language wiki MUST follow this structure. **Concepts should be taught directly through mirrored implementation code boxes.**

---

## Definition
Teach the concept in plain English directly above the code box. 
- **Complexity Rule:** If the topic is simple, keep it brief. If it is critical or complex, explain as much as needed to ensure proper understanding before implementation.

## 1. Legacy Way / Conventional Path (The "Auto" Path)
Show the most common, high-level way the language handles this feature.
- **Focus:** Speed, simplicity, and the "Default" behavior.
- **Output:** Every output action MUST have a `// Output: ...` comment.

## 2. Modern Way / Explicit Path (MANDATORY)
Show how to make the logic explicit and strict. This section is vital for languages that are "auto" or dynamic.
- **Mirror Rule:** Perform the EXACT SAME TASK as the Conventional Path above.
- **Type Safety:** Explicit type annotations (e.g., `int x = 10`).
- **Input/Output Clarity:** Explicit **Parameter Types** and **Return Types** for functions.
- **Memory Clarity:** Explicit markers for **Value** vs. **Reference**.
- **Output:** Include `// Output: ...` comments.

# The Logic Bridge
A one-sentence note (comment) explaining what the language does "automatically."
- **Goal:** To remove the "Magic."
- **Example:** "// Logic: The interpreter identifies this as an integer based on the literal."
