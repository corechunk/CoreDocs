# 🟢 Milestone 34: Structs - Base [CORE]

### 1. Record Grouping
A Struct is a way to group related data (like a User's ID, Name, and Email) into a single logical unit. Since Bash has no native `struct` keyword, we use **Associative Arrays** to create record namespaces.

```bash
# CONVENTIONAL: Loose prefixing (Anti-pattern)
user1_name="Bob"; user1_id=42 # Logic: Fragile and unscalable

# EXPLICIT: Associative Record
declare -A User1=(
    [name]="Bob"
    [id]=42
    [role]="Admin"
)

# Logic: By using a single array name for all related fields, 
# you create a memory-managed record that can be passed as a 
# single handle.
```

### 2. Struct Handlers
To act on these simulated structs, pass the **Name** of the array to a function and use a nameref to dereference it.

```bash
# EXPLICIT: Struct "Method"
function print_user() {
    local -n u=$1           # 'u' points to the array name passed
    echo "User: ${u[name]} (ID: ${u[id]})"
}

print_user User1            # Logic: Passes "User1" string
```
