# Security Best Practices: Temporary Files

In Linux systems engineering, how you manage temporary files defines the security of your installer. Hardcoding paths in `/tmp` is a common mistake that leads to "System Destroyer" vulnerabilities.

---

## 🛑 The "Hardcoded /tmp" Anti-Pattern
**Never do this:**
```bash
# VULNERABLE: Race Condition Vulnerability
TMP_DIR="/tmp/my-app-installer"
mkdir -p "$TMP_DIR"
```

### Why it's a security hole:
1.  **Race Conditions:** If a malicious user knows your script uses `/tmp/my-app-installer`, they can pre-create that directory with `777` permissions and put a malicious file inside *before* your script runs. Your script might then execute the attacker's code.
2.  **Collisions:** If two users run your installer simultaneously, they will clash over the same directory, causing unexpected failures.

---

## 🏆 The "Pro-Tier" Solution: `mktemp`

`mktemp` is the industry standard for creating ephemeral, secure temporary files and directories.

### Secure Implementation:
```bash
# SECURE: Creates a unique, random directory
TMP_DIR=$(mktemp -d)

# Ensure it's cleaned up even if the script crashes
trap 'rm -rf "$TMP_DIR"' EXIT

# Now safe to use
echo "Working in $TMP_DIR"
```

### Why `mktemp` wins:
1.  **Guaranteed Uniqueness:** It generates a random string (e.g., `/tmp/tmp.a1B2c3D4e5`), ensuring no collision with other users or files.
2.  **Restrictive Permissions:** It automatically sets the correct, restrictive permissions (`700`), so only the user who created the directory can read or write to it.
3.  **Atomic Creation:** `mktemp` creates the directory *and* guarantees it didn't exist before in a single atomic operation.

---

## ⚠️ The Verdict: Why Manual Randomization Fails

You might wonder: *"Can I just create a random string myself, like `mkdir /tmp/app-$(head /dev/urandom | ...)`?"*

**Verdict: Do not do this.** 

Even if you make the name highly random, you are violating the principle of **Atomicity**.

### The "Time-of-Check to Time-of-Use" (TOCTOU) Flaw:
If you do this:
```bash
# VULNERABLE: Not Atomic
DIR="/tmp/app-$(random_string)"
mkdir "$DIR"
chmod 700 "$DIR"
```
There is a tiny, but fatal, window of time between `mkdir` and `chmod`. 
1.  Script runs `mkdir`.
2.  **Attacker exploits that microsecond** to modify the permissions of that directory before your `chmod` runs.
3.  Your script continues, believing the directory is secure, while the attacker now has control.

**`mktemp` is superior because it is atomic.** It creates the directory **and** sets the permissions in a single operation that the OS kernel guarantees cannot be interrupted. In systems engineering, **if a tool exists to handle atomicity, use it.**

## 🆔 Identity Footprinting & Provider Verification

Before an installer performs destructive actions (like overwriting or deleting a binary during conflict resolution), it MUST verify that the binary belongs to the same provider.

### The "--identity" Flag Strategy
Implementing a hidden diagnostic flag in the application is the most reliable way to confirm ownership.

1.  **The Flag:** `app --identity` returns a unique string like `corechunk/app`.
2.  **The Verification:** The installer runs:
    ```bash
    if [path/to/binary --identity 2>/dev/null | grep -q "corechunk"]; then
        # Proceed with managed update
    else
        # Critical warning: Foreign binary detected with same name
    fi
    ```

### Why Verification Matters
*   **Name Collisions:** Prevents accidental deletion of a different tool that shares the same name.
*   **Distribution Awareness:** Distinguishes between a manually installed version (yours) and one managed by a system package manager (e.g., an AppImage or Snap).
