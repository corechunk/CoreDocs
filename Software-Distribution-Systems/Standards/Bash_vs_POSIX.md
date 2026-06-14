# Bash vs. POSIX: The Installer Philosophy

If your software is a pure Bash script, you might wonder: *"Since I am using Bash, do I need to be strictly POSIX compliant?"*

---

## ⚖️ The Verdict: "Target the Lowest Common Denominator"

While your **application** might require Bash features (arrays, process substitution, etc.), your **Installer** should ideally aim for high compatibility (POSIX or near-POSIX).

### Why POSIX-Compliant Installers Win:
1.  **The "Shebang" Problem:** Even if you write `#!/bin/bash`, if the user runs your script as `sh install.run`, many systems (especially Debian/Ubuntu) will interpret it with `dash` (a strict POSIX shell), not `bash`. Your script will likely syntax error immediately.
2.  **Universal Execution:** If your installer is strictly POSIX, it will run correctly whether the user triggers it with `bash install.run`, `sh install.run`, or `./install.run` on an Alpine Linux system where `sh` is `ash`.
3.  **Pro-Tier Resilience:** It shows you are an engineer who builds for the **infrastructure**, not just for your specific environment.

---

## 🔍 Shebang Strategy: `/bin/sh` vs `env`

When writing your POSIX installer, the shebang determines which interpreter is used.

### The Verdict:
*   **Use `#!/bin/sh` for Infrastructure (Traditional FHS):** 
    *   **Why?** The FHS (Filesystem Hierarchy Standard) *mandates* that `/bin/sh` exists on every traditional POSIX-compliant system. It is the bedrock of the OS.
    *   **Do NOT use `#!/bin/dash` or `#!/bin/bash`:** These are absolute paths. If the user is on a system where that shell is installed elsewhere (or not at all), your script breaks.
*   **Use `#!/usr/bin/env sh` for Modern/Immutable Infrastructure (NixOS):** 
    *   **Why?** On modern immutable/atomic distributions like NixOS, the standard `/bin/sh` path often **does not exist** or is non-standard. Using `#!/usr/bin/env sh` allows the shell to be resolved dynamically from the user's environment.
*   **Use `#!/usr/bin/env bash` for your Application:**
    *   **Why?** This is only used for the *application payload* (the script you install), not the *installer script itself*. It dynamically locates the `bash` interpreter in the user's `$PATH`.

**Pro-Tier Verdict:** 
Use `#!/bin/sh` if you prioritize strict FHS compliance for traditional distros. Use `#!/usr/bin/env sh` if you prioritize maximum portability across modern, immutable/Nix-style environments. Both are POSIX-compliant.

---

## 💡 The "Pro-Tier" Strategy: The Split-Layered approach

1.  **The Installer Layer:** Keep this strictly POSIX.
    *   **Shebang:** `#!/bin/sh`
    *   **Logic:** No arrays, no `[[ ]]`, no `function` keyword (use `name() { ... }`).
2.  **The Application Layer:** Once deployed, your app can use Bash features.
    *   **Shebang:** `#!/usr/bin/env bash`

### Checklist for a Portable Installer:
*   [ ] **Use `.` instead of `source`**: POSIX compliant and universally available.
*   [ ] **Avoid `[[ ]]`**: Use `[ ]` for conditional tests.
*   [ ] **Avoid Arrays**: Use positional parameters (`$1`, `$2`) or simple string manipulation.
*   [ ] **Strict Shebang**: Use `#!/bin/sh`.

**Summary:** Your installer script should be as **boring and compatible as possible** to guarantee it works on every Linux box, while your application code is free to be as powerful as Bash allows.
