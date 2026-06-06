# 🔵 Milestone 15: Pattern Matching [PRO]

### 1. Globbing (The Basics)
Pattern matching checks if a string conforms to a specific "Shape." Globbing is the simplest form, used primarily for file discovery.

```bash
# CONVENTIONAL: Basic wildcards
ls *.txt                    # Match any filename ending in .txt

# EXPLICIT: Extended Globs
shopt -s extglob            # Enable advanced features
if [[ $file == *.@(jpg|png) ]]; then 
    echo "Image found"
fi

# Logic: The shell's Glob Engine scans the directory or string 
# using simple state-machine matching (?, *, [ ]).
```

### 2. Regex (The Heavy Hitter)
For complex validation (like verifying an IP address or email), Bash provides native Regular Expression matching using the same engine as many systems languages.

```bash
# EXPLICIT: Native Regex
input="192.168.1.1"
if [[ $input =~ ^[0-9]{1,3}\.[0-9]{1,3} ]]; then
    echo "Valid prefix"
fi

# Logic: Bash uses the system's regex.h library. Match results 
# for capturing groups are stored in the BASH_REMATCH array.
```

### 3. Native Regex Breakdown (=~)
The `=~` operator allows for direct pattern testing within `[[ ]]`.

#### The Anatomy of `[[ $var =~ ^[0-9]+$ ]]`
- **`^`** (Caret): Start of string anchor.
- **`$`** (Dollar): End of string anchor.
- **`[ ]`** (Brackets): Character class (set of allowed characters).
    - `[0-9]` : Any digit.
    - `[a-z]` : Any lowercase letter.
- **`+`** (Plus): Quantifier - "One or more".
- **`*`** (Asterisk): Quantifier - "Zero or more".
- **`?`** (Question): Quantifier - "Zero or one" (Optional).

| Example | Matches | Logic |
| :--- | :--- | :--- |
| `^[0-9]+$` | "123", "7" | Numeric only, start-to-finish. |
| `^[0-9]$` | "5", "0" | **Exactly one** digit. |
| `^[a-zA-Z]+$`| "Hello" | Alphabetic only. |

**Pro Tip**: Do **not** quote the regex pattern on the right side if you want it to behave as a regex.

