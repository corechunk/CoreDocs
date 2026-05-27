# Template: Compilation & Execution Basics [CORE]

**Goal:** To define the minimal ritual for transforming a source file into a running program and verifying the health of the toolchain.

---

## 1. The Definition (Mental Model)
The wiki must start by explaining the "Execution Cycle."
- **What is it?** The process of telling the computer to read your text file and perform the actions described inside.
- **Compiled vs. Interpreted:** Briefly explain if the language needs a build step (C/C++) or runs directly from the script (Bash/Python).

## 2. Requirement: The Build Command (Compiled)
Document the standard command to create an executable.
- **Syntax:** (e.g., `gcc main.c -o app`).
- **Flags:** Explain the `-o` (Output) flag and any other mandatory parameters.

## 3. Requirement: The Run Command
Document how to start the process.
- **Binary:** (e.g., `./app`).
- **Interpreter:** (e.g., `bash script.sh` or `python main.py`).
- **Permissions:** Note if `chmod +x` is required for the OS to allow execution.

## 4. Requirement: The "Health Check" Snippet
Provide the absolute simplest code to verify the setup (e.g., printing "OK").
- **Goal:** If this runs, the toolchain is perfect.

## 5. Documentation Checklist
- [ ] Command to build (if applicable).
- [ ] Command to run.
- [ ] Minimalist code snippet.
- [ ] Troubleshooting: (e.g., "Command not found" error).
