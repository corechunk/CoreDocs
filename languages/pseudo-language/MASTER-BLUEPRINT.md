# 🏛️ Master Blueprint: Structural Guide for Language Wikis

**Purpose:** This is the authoritative guide for generating the definitive **`master-<language-name>.md`** Master File in each language directory. It ensures that **ALL topics tagged as [CORE]** from the 53 universal logic milestones are captured in a high-density, mirrored learning format.

---

## 🏗️ The "Gold Standard" Entry Format (Codebox-Centric)
Every topic (especially **[CORE]** topics) must follow this 4-step structure to ensure perfect pedagogical mirroring. Information MUST be taught directly through implementation code boxes.

### Definition
A concise "What & Why" (un-numbered). If the topic is critical or complex, explain as much as needed to ensure the concept is understood before moving to the implementation.

### 1. Legacy Way (Version) / Conventional Path
- **For C/C++:** Show the established older standard (e.g., C99 / C11 / C17).
- **For Dynamic Languages (Bash/Lua):** Show the most common, high-level syntax (The "Auto" Path).
- **Rule:** Snippets MUST be self-contained (include necessary headers/setup).
- **Output:** Every `printf` or output action MUST have a `// Output: ...` comment.

### 2. Modern Way (Version) / Explicit Path
- **For C/C++:** Show the latest standard (e.g., C23).
- **For Dynamic Languages:** Show the strict, type-safe, or manual syntax (The **Explicit Way**). 
- **Mirror Rule:** This snippet MUST perform the **EXACT SAME TASK** as the snippet above to highlight the evolution or the hidden "Magic" (e.g., explicit typing in a dynamic language).
- **Output:** Include `// Output: ...` comments.
- **Native Logic:** Explicitly state if headers are no longer needed (for native keywords).

### # The Logic Bridge
A single-line or brief comment explaining what the system (Compiler/Kernel/Interpreter) is doing "under the hood" (un-numbered).

---

## 📂 The Expansion Pattern (Hub-and-Spoke)
If a **[CORE]** milestone is technically dense or requires exhaustive tables (e.g., Data Types, Operators, Collections), it MUST be split into a sub-directory.

1.  **The Hub File:** The primary milestone file (e.g., `09-data-types.md`) remains the high-level conceptual entry point. It MUST contain the mirrored comparison and high-signal examples.
2.  **The Spoke Files:** A sub-directory named after the topic (e.g., `/data-type/`) stores granular deep-dives (e.g., `integers.md`).
3.  **Redirection:** The Hub file MUST provide clear links to its Spoke files for exhaustive technical reference.

---

## 📋 Mandatory Core Components
- [ ] **Mirrored Logic:** Both snippets doing the exact same work.
- [ ] **Output Comments:** `// Output: ...` for every result.
- [ ] **Explicitness:** Showing the "Strict" way for dynamic languages.
- [ ] **Version Precision:** Clearly stating C23 vs Legacy where applicable.
