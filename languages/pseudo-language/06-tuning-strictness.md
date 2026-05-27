# Template: Tuning & Strictness [PRO]

**Goal:** To define how to configure the language engine (compiler or interpreter) for maximum safety, standard compliance, and early bug detection.

---

## 1. The Definition (Mental Model)
The wiki must start by explaining the concept of "Strictness."
- **What is it?** Programming languages often allow "lazy" code by default. Tuning strictness is the act of turning on the "Guardrails."
- **Why?** It catches logical errors (like using uninitialized variables) during the build process rather than letting the program crash at runtime.

## 2. Requirement: Toolchain Flags (Compiled Languages)
Document the flags passed to the compiler to enforce rules.
- **Warning Levels:** (e.g., `-Wall`, `-Wextra` in C).
- **Fatal Warnings:** (e.g., `-Werror` - treats every warning as a crash-worthy error).
- **Standard Enforcement:** (e.g., `-std=c11`, `-pedantic`).

## 3. Requirement: Interpreter Modes (Scripting Languages)
Document commands or environment variables that change execution behavior.
- **Fail-Fast:** (e.g., `set -e` in Bash to stop on first error).
- **Unbound Check:** (e.g., `set -u` to stop if a variable is used before it is defined).
- **Standards Mode:** (e.g., `set -o posix`).

## 4. Documentation Checklist
- [ ] Clear definition of "Strictness."
- [ ] A "Recommended Golden Set" of flags/commands for every project.
- [ ] Explanation of the trade-off: (Slower development vs. Rock-solid stability).
