# 🔵 Milestone 46: Redirection & Piping [PRO]

### 1. Stream Rerouting
Redirection is the act of sending a process's mouth (stdout) or megaphone (stderr) to a file instead of the terminal.

```bash
# EXPLICIT: File Output
ls > files.txt              # Overwrite stdout
cat data.txt >> log.txt     # Append stdout
mkdir /tmp 2> errors.log    # Redirect stderr only

# Logic: Bash opens the file and replaces the process's file 
# descriptor 1 or 2 with the new file's descriptor.
```

### 2. Inter-Process Glue
Piping connects the mouth of one program to the ear of another, allowing you to build complex logic from small, specialized tools.

```bash
# EXPLICIT: The Pipe Chain
cat access.log | grep "404" | wc -l

# EXPLICIT: Advanced Redirection
command &> all.log          # Combined stdout/stderr
command > /dev/null 2>&1    # Silence (The "Void")

# Logic: '|' creates a Kernel Buffer (Pipe). The OS connects 
# FD 1 of the left process to the write-end and FD 0 of the right 
# process to the read-end in memory.
```
