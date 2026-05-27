Bash is less of a standard programming language and more of a glue language. It operates by passing text streams between discrete tools. To master it, you need to separate **Pure Bash** (built-in syntax and parameter expansion) from **External Commands** (sed, awk, grep).
Here is your comprehensive cheat sheet for Bash syntax, conditional constructs, and text parsing.
### 1. The Bracket Multiverse (Conditions & Contexts)
Bash uses different brackets for entirely different execution contexts. This is the most common source of confusion.

| Syntax    | Name             | Purpose & Rules                                                                      | Example                        |
| --------- | ---------------- | ------------------------------------------------------------------------------------ | ------------------------------ |
| [ ... ]   | POSIX Test       | Old, portable. Variables *must* be quoted.                                           | if [ "$a" = "yes" ]; then      |
| [[ ... ]] | Bash Test        | Modern, safer. No word splitting. Supports regex (=~) and wildcards (== *txt).       | if [[ $a == *.txt ]]; then     |
| (( ... )) | Arithmetic       | C-style math. No $ needed for variables inside. Returns 0 (true) if math > 0.        | if (( a > 5 && b == 2 )); then |
| ( ... )   | Subshell         | Runs commands in a child process. Variables changed inside do not affect the parent. | (cd /tmp && rm *.log)          |
| ${ ... }  | Expansion        | Variable manipulation, defaults, and pure bash string parsing.                       | echo "${var:-default_val}"     |
| $( ... )  | Cmd Substitution | Runs a command and captures its standard output into a variable or string.           | files=$(ls -1)                 |
### 2. Pure Bash String Parsing (Parameter Expansion)
You do not always need sed or awk. Bash has built-in string manipulation that is orders of magnitude faster because it doesn't spawn an external process.
```bash
filepath="/var/log/nginx/access.log"

# 1. Substrings
echo "${filepath:5:3}"    # Starts at offset 5, length 3 -> "log"
echo "${filepath: -4}"    # Last 4 characters -> ".log" (Notice the space!)

# 2. Stripping Prefixes (Front)
echo "${filepath#*/}"     # Shortest match: removes first "/" -> "var/log/nginx/access.log"
echo "${filepath##*/}"    # Longest match: removes everything up to last "/" -> "access.log" (Like 'basename')

# 3. Stripping Suffixes (Back)
echo "${filepath%.*}"     # Shortest match: removes extension -> "/var/log/nginx/access"
echo "${filepath%%/*}"    # Longest match: removes from first "/" backwards -> (Empty string here)

# 4. Search and Replace
echo "${filepath/log/run}"  # Replace FIRST instance -> "/var/run/nginx/access.log"
echo "${filepath//log/run}" # Replace ALL instances -> "/var/run/nginx/access.run"

```
### 3. Pure Bash File Parsing
The safest and most standard way to parse a file line-by-line purely in Bash is the while read loop.
```bash
# IFS= (Internal Field Separator cleared) prevents trimming leading/trailing whitespace.
# -r prevents backslashes from being interpreted as escape characters.

while IFS= read -r line; do
    
    # Skip empty lines
    [[ -z "$line" ]] && continue 
    
    # Skip commented lines (using Bash pattern matching)
    [[ "$line" == \#* ]] && continue 
    
    # Process line
    echo "Processing: $line"

done < "input.txt"

```
### 4. The Heavy Lifters: External Parsing Tools
When Pure Bash isn't enough, you pipe (|) data into these tools.
#### grep (Line Filtering)
Used to find or exclude lines based on patterns.
```bash
grep "ERROR" file.log        # Print lines containing ERROR
grep -v "DEBUG" file.log     # Print lines NOT containing DEBUG
grep -i "error" file.log     # Case-insensitive
grep -E "^[0-9]+" file.log   # Extended regex (starts with numbers)

```
#### cut (Delimiter Splitting)
Best for simple, perfectly structured data (like CSVs).
```bash
# -d: sets delimiter to colon. -f1,3 extracts columns 1 and 3.
echo "root:x:0:0:root" | cut -d: -f1,3  # Outputs: root:0

```
#### awk (Column & Logic Parsing)
A complete programming language. It auto-splits lines into variables $1, $2, $3 based on whitespace.
```bash
# Print the 2nd column of the file
awk '{print $2}' file.txt 

# Print the 1st column ONLY if the 3rd column is greater than 50
awk '$3 > 50 {print $1}' file.txt 

# Change the output delimiter (OFS) to a comma
awk 'BEGIN {OFS=","} {print $1, $3}' file.txt

```
#### sed (Stream Editor)
Best for finding/replacing text or extracting specific line numbers.
```bash
# Replace 'foo' with 'bar' on every line (s = substitute, g = global)
sed 's/foo/bar/g' file.txt 

# Delete lines 5 through 10
sed '5,10d' file.txt 

# Extract only lines 10 to 20
sed -n '10,20p' file.txt 

# In-place edit (overwrites the file directly)
sed -i 's/foo/bar/g' file.txt

```
### 5. Control Flow & Standard Constructs
```bash
# IF / ELIF / ELSE
if [[ -f "config.json" ]]; then
    echo "File exists"
elif [[ -d "config" ]]; then
    echo "Directory exists"
else
    echo "Neither found"
fi

# CASE (Switch statement)
read -r -p "Continue? [y/N]: " answer
case "$answer" in
    [Yy]* ) echo "Proceeding...";;
    [Nn]* ) echo "Aborting."; exit 1;;
    * )     echo "Invalid input.";;
esac

# FOR LOOP (Iterating lists or arrays)
for item in apple banana cherry; do
    echo "Fruit: $item"
done

# FOR LOOP (C-Style)
for (( i=0; i<5; i++ )); do
    echo "Count: $i"
done

```
### 6. File Descriptors & Redirection
Everything in Linux is a file, including standard outputs and errors.
 * 0 = Standard Input (STDIN)
 * 1 = Standard Output (STDOUT)
 * 2 = Standard Error (STDERR)
```bash
echo "data" > file.txt       # Overwrite STDOUT to file
echo "data" >> file.txt      # Append STDOUT to file
grep "fail" < file.txt       # Read STDIN from file

# Error handling
command 2> errors.log        # Redirect ONLY errors to file
command > output.log 2>&1    # Redirect STDOUT and STDERR to the same file
command &> all.log           # Bash shortcut for the above line
command > /dev/null 2>&1     # Throw all output and errors into the void

```
Which specific text processing tool or parsing method are you finding the most difficult to implement in your current scripts?
