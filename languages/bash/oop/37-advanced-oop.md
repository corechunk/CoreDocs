# 🔵 Milestone 37: Advanced OOP [PRO]

### 1. Data Encapsulation
Encapsulation involves hiding internal state from the user. In Bash, this is achieved by convention and by restricting access through specialized "Method" functions.

```bash
# EXPLICIT: Private Convention
# Use '__' prefix for internal fields
declare -A User=( [__db_id]="12345" [name]="Alice" )

# Logic: Since Bash has no true private scope, encapsulation is 
# enforced by the programmer's discipline and naming rules.
```

### 2. Method Dispatch
Methods are functions that act specifically on an object instance. We use **Namespace Prefixing** to associate logic with a simulated class.

```bash
# EXPLICIT: Class Method
function User.set_role() {
    local -n self=$1         # The 'this' pointer
    local new_role=$2
    self[role]="$new_role"
}

# CALLING
User.set_role "user_42" "Admin"

# Logic: Namespace prefixing (User.xxx) prevents collision in the 
# global function table and mimics the 'dot notation' of 
# systems languages.
```
