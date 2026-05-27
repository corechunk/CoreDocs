Bash is less of a standard programming language and more of a glue language. It operates by passing text streams between discrete tools. To master it, you need to separate **Pure Bash** (built-in syntax and expansion) from **External Commands** (sed, awk, grep).
Here is your comprehensive, compact master reference for Bash, covering the full 53-milestone lifecycle using dense implementation blocks.

### 1. Environment, Ritual & Strictness
Bash is an interpreter. Shebangs and permissions transform text into programs. Strictness flags act as the "Guardrails" to catch logical errors before they cause data loss.
```bash
#!/usr/bin/env bash  # Portable Shebang
# chmod +x script.sh # Grant Permission

set -euo pipefail    # SAFE MODE: Exit on error, unbound vars, and pipe failures
shopt -s inherit_errexit # Bash 4.0+: Pass -e into subshells

# INSTALL: mise use bash@latest | sudo apt install bash
# VERIFY: bash --version | which bash
```

### 2. Lexical Atoms, Charset & Metadata
"Everything is a string." Whitespace is a functional separator. Attributes like `Integer` or `Read-only` are interpretation flags. Locale determines how bytes become characters (UTF-8).
```bash
# LOCALE: export LANG=en_US.UTF-8 (Force UTF-8 interpretation)
# ASSIGNMENT: NO SPACES around '='
user="Alice" 

# TYPE (declare): Keywords vs Built-ins
type if     # Keyword
type cd     # Built-in
type ls     # External binary

# METADATA: Heredoc trick for blocks
: ' 
  DESCRIPTION: Master Script
  VERSION: 1.0.0
'
```

### 3. Variables, Constants & Attributes
Attributes are set in the symbol table to trigger specific shell behaviors. Constants are write-protected entries that cannot be unset or reassigned.
```bash
# ATTRIBUTES
declare -i age=25  # Integer (Triggers math context on assignment)
declare -r PI=3.14 # Read-only (Constant)
declare -l low="A" # Lowercase auto-convert
declare -u up="b"  # Uppercase auto-convert

# STORAGE (SYSTEMS)
export API_KEY="X" # Environment (Shared with children)
# declare -p age    # Inspect attributes
```

### 4. String Mastery & Interpolation
Bash performs high-performance text manipulation in-memory during the Expansion Phase, bypassing expensive external tools like `sed` or `awk`.
```bash
path="/var/log/app.log"

# EXPANSION (Interpolation)
echo "${user:-Guest}" # Fallback if empty
echo "${user:?Error}" # Exit if empty

# STRIPPING (Front/Back)
echo "${path##*/}" # Basename: "app.log" (Longest match front)
echo "${path%.*}"  # No Ext: "/var/log/app" (Shortest match back)

# SLICING & REPLACE
echo "${str:0:5}"      # Substring: offset 0, length 5
echo "${str//log/run}" # Replace ALL instances

# ESCAPING
echo $'Line 1\nLine 2' # ANSI-C Quoting
```

### 5. Scope, Subshells & Contexts
Scope determines visibility. Subshells create isolated process clones. Changes in a subshell cannot travel "backwards" to the parent process.
```bash
# GLOBAL: Default behavior
x=10 

function demo_scope() {
    local x=20 # Scoped to function
}

# ISOLATION (Fork)
( x=30; cd /tmp ) # Runs in child process
echo $x # Still 10
# Current Dir is unchanged
```

### 6. Operations & The Bracket Multiverse
Bash chooses between the Arithmetic Engine `(( ))` and the Logical Test Engine `[[ ]]`. Casting is implicit based on the evaluation context.
```bash
# ARITHMETIC (( )) - C-style math, no $ needed
(( sum = x + (5 * 2), count++ ))

# LOGIC [[ ]] - Modern test context, supports regex
if [[ -f $file && $user == "root" ]]; then :; fi
if [[ $path =~ ^/var/ ]]; then :; fi # Regex Match

# CASTING: Hex string to Int
hex="0x0A"
(( dec = hex )) # dec is now 10
```

### 7. Logical Flow & Truth Rules
Bash uses "Inverted Truth": **0 is Success (True)**. Decision points branch based on the process return status register.
```bash
# TRUTH RULE
# Success (0) is True; Error (1-255) is False
[ -d "/tmp" ] && echo "Exists" || exit 1 # Short-circuit

# CONDITIONALS
case "$1" in 
    (start) ./run ;; 
    (stop)  exit 0 ;; 
    (*)     echo "usage" ;;
esac

# JUMPS: break n (loop level), continue n, return 0 (func), exit 0 (script)
```

### 8. Iteration & File Parsing
Loops iterate over Words (for) or Success (while). Safe file parsing requires clearing the IFS to prevent whitespace trimming.
```bash
# SAFE FILE PARSING (while read)
while IFS= read -r line; do
    echo "$line"
done < "file.txt"

# ARRAY ITERATION (Always quote expansion!)
for item in "${list[@]}"; do
    echo "Item: $item"
done

# DEFINITE: for (( i=0; i<10; i++ )); do :; done
```

### 9. Function Engine & Data Passing
Functions return an **Exit Status**, not data; data is "Returned" via stdout. `nameref` allows pass-by-reference.
```bash
# ENGINE
function get_user() {
    local id=$1 # Positional Param
    local -n ref=$2 # Nameref (Pointer to variable name)
    echo "user_$id" # "Return" data via stdout
    ref="processed" # Modify original variable
    return 0 # Success status
}

# USAGE
my_status="none"
current_user=$(get_user 42 my_status) # Capture stdout, update status
```

### 10. Collections: Arrays & Maps
Grouping data into sequences or key-value hash tables. Bash arrays are sparse linked-lists of strings.
```bash
# INDEXED ARRAY (Sequence)
list=(a b c); list[100]="sparse"

# ASSOCIATIVE ARRAY (Map/Hash)
declare -A user_map=([name]="Bob" [id]=42)

# ACCESS
echo "${list[@]}"      # All values
echo "${!user_map[@]}" # All keys
echo "${#list[@]}"     # Count

# BULK LOAD: mapfile -t arr < file.txt
```

### 11. Architecture: Structs & Simulated OOP
Bash simulates OOP and Structs by dynamically generating uniquely named associative arrays and using namerefs for method dispatch.
```bash
# SIMULATED CONSTRUCTOR
function User.new() {
    local id=$1; local var_name="user_$id"
    declare -g -A "$var_name" # Global instance
    local -n self="$var_name"
    self[id]=$id; self[role]="User"
    echo "$var_name" # Return Handle
}

# METHOD
function User.set_role() {
    local -n self=$1
    self[role]=$2
}

handle=$(User.new 101); User.set_role "$handle" "Admin"
```

### 12. OS Bridge: Streams & Redirection
The "Whole Funda" of process communication. Bash manipulates the process file descriptor table to glue tools together.
```bash
# STREAMS: 0 (stdin), 1 (stdout), 2 (stderr)
echo "Error" >&2  # Write to Stderr
cmd > log 2>&1    # Combine Stdout/Stderr to one file
cmd &> all.log    # Bash shortcut for above

# PIPES & REDIRECTION
cat data | grep "x" # Connect FD 1 of A to FD 0 of B
cmd <<< "string"    # Herestring (stdin)
cmd <<EOF           # Heredoc
multi-line
EOF
```

### 13. Concurrency, Async & Locking
Bash manages the process lifecycle via forks. Locks ensure atomic access to shared system resources.
```bash
# FORK & WAIT
./task.sh & pid=$! # Background (fork)
wait $pid # Block parent until child finishes

# COPROCESS: Two-way pipe (Async)
coproc WORKER { bc; }
echo "10+10" >&"${WORKER[1]}"; read -r res <&"${WORKER[0]}"

# LOCKING (Advisory)
( flock -x 200; echo "Critical Logic" ) 200>/var/lock/mylock
```

### 14. Networking: Raw Streams & APIs
Direct socket communication via the virtual file system. APIs are integrated using the Unix Philosophy (curl + jq).
```bash
# RAW TCP (SYSTEMS)
exec 3<>/dev/tcp/google.com/80
echo -e "GET / HTTP/1.1\n\n" >&3
head -n 1 <&3; exec 3>&- # Close

# API (PRO)
# Uses external tools as "Standard Library"
json=$(curl -s https://api.github.com/users/netchunk)
name=$(echo "$json" | jq -r '.name')
```

### 15. Lifecycle, Memory & Delivery
Project orchestration and maintenance. Memory is managed via unsetting. Delivery often uses self-extracting polyglots.
```bash
# MEMORY: unset var (Immediate free)
# LINTER: shellcheck script.sh (Essential for PRO scripts)

# MULTI-FILE: Relative sourcing
readonly ROOT=$(dirname "$(readlink -f "$0")")
source "$ROOT/lib/core.sh"

# ERROR TRAP
trap 'echo "Error at $LINENO"' ERR
trap 'rm /tmp/lock' EXIT # Signal cleanup
```
