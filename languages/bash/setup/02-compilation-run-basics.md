# 🟢 Milestone 02: Execution Ritual [CORE]

### 1. Basic Invocation
Execution is the act of telling the Operating System to hand your text file to the `bash` interpreter. Since scripts are just text, you can call the interpreter and pass the file name as a "payload."

```bash
# CONVENTIONAL: Run as an argument (No permissions needed)
bash my_script.sh

# Logic: This bypasses the Shebang and uses the 'bash' binary 
# currently in your focus to read the text file.
```

### 2. First-Class Executables
To make a script act like a "Real" program, you must tell the OS which interpreter to use and grant the file "Execution" permission bits.

```bash
# EXPLICIT: The Shebang (Line 1 of the file)
#!/usr/bin/env bash        # Portable path via 'env'

# EXPLICIT: Granting Permissions
# chmod +x my_script.sh    # Add the 'x' bit to the file metadata

# EXECUTION
./my_script.sh             # Execute directly as a command

# Logic: The Kernel reads the first two bytes (#!). If they match, 
# it treats the rest of the line as the path to the loader (bash) 
# and hands it the file.
```
