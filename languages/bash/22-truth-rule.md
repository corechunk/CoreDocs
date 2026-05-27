# 🟢 Milestone 22: Truth Rule [CORE]

### 1. Inverted Boolean Logic
In most programming languages, `1` is True and `0` is False. In Bash, the logic is **Exactly Inverted**. Bash cares about process outcomes, not boolean literals.

```bash
# SUCCESS (True)
# A return code of 0 means "Success" or "No Errors".

# FAILURE (False)
# Any return code from 1 to 255 means "Error".

# Logic: Bash flow control keywords (if, while) execute a 
# command and look at the CPU's Status Register. A zero in the 
# register triggers the "True" branch.
```

### 2. Manual Verification
You can inspect the success or failure of the last executed command using the special `$?` variable. This is the "Manual" way to verify logic.

```bash
# EXPLICIT: Status Inspection
grep -q "pattern" file.txt
status=$?

if (( status == 0 )); then
    echo "Pattern Found (Success/True)"
fi

# Logic: $? is a temporary placeholder that is overwritten by 
# every single command execution. Always capture it immediately.
```
