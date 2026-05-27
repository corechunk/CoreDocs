# 🟢 Milestone 01: Toolchain Installation [CORE]

### 1. The Shell Interpreter
Bash (Bourne Again SHell) is an interpreter that acts as both a command language and a programming language. Unlike compiled languages, the "Toolchain" is simply the `bash` binary itself, which reads and executes scripts line-by-line.

```bash
# CONVENTIONAL: System-native installation
sudo apt install bash      # Linux (Debian/Ubuntu)
sudo pacman -S bash        # Linux (Arch)
brew install bash          # macOS (Latest v5+)

# WINDOWS: The Git Bash way
# Download "Git for Windows" from git-scm.com.
# It includes a MinGW-based Bash environment.

# Logic: The shell binary is loaded into memory by the Kernel 
# to process text streams as functional instructions.
```

### 2. Version Management
Because Bash evolves (e.g., Bash 4.0 added associative arrays), managing specific versions is critical for script portability and consistency across environments.

```bash
# EXPLICIT: Manage versions via 'mise'
mise use bash@latest       # Set local/global version

# VERIFICATION
which bash                 # Locate binary path in PATH
bash --version             # Confirm exact version string

# Logic: The OS looks through the PATH variable to find the first 
# executable named 'bash'. Version managers like mise manipulate 
# this PATH to point to your desired version.
```
