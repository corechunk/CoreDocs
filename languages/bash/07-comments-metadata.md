# 🟢 Milestone 07: Comments & Metadata [CORE]

### 1. Human-Readable Notes
Comments are sections of source code ignored by the shell. They should explain the *Reasoning* (the "Why") behind a specific implementation, not what the syntax already shows.

```bash
# CONVENTIONAL: Single line
# Calculate total excluding tax
echo "Logic"               # Inline comment

# Logic: When the parser encounters an unquoted '#', it discards 
# all remaining bytes on that line in its input buffer.
```

### 2. Machine-Readable Directives
Metadata provides "Out-of-band" instructions to the Kernel or the Shell itself. This includes identifying the interpreter and documenting script properties for maintenance.

```bash
# EXPLICIT: Mandatory Metadata
#!/usr/bin/env bash        # The Shebang (Kernel Directive)

# EXPLICIT: Block Documentation (Heredoc trick)
: '
  DESCRIPTION: Clean-up script for logs
  VERSION: 2.1.0
  DEPENDS: coreutils, grep
'

# Logic: The ':' (null command) treats the string as an argument 
# but does nothing with it, effectively creating a multi-line 
# block that is stored in RAM but never executed.
```
