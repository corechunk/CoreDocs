# Template: Toolchain Installation [CORE]

**Goal:** To define the step-by-step procedures for installing the language engine (compiler or interpreter) on any operating system.

---

## 1. The Definition (Mental Model)
The wiki must start by explaining the "Toolchain."
- **What is it?** Your text editor is just for writing. The toolchain is the "Factory" (Compiler) or "Translator" (Interpreter) that turns your text into a running program.
- **Why?** Without these tools, your code is just a text file.

## 2. Requirement: OS-Specific Procedures
Provide exact commands for the three major platforms.
- **Linux:** (e.g., `sudo apt install build-essential` or `sudo pacman -S gcc`).
- **Windows:** (e.g., Installing MinGW, using WSL2, or a standalone `.exe`).
- **macOS:** (e.g., `brew install ...`).

## 3. Requirement: Modern Version Management
Document the "Pro" way to handle toolchains using version managers.
- **Tools:** (e.g., `mise`, `asdf`, `nvm`, `rustup`).
- **Commands:** How to install a specific version using the tool.

## 4. Requirement: PATH & Verification
Explain how to tell the OS where the tool is.
- **PATH Setup:** If manual installation, provide the `export PATH=...` syntax.
- **Verification:** The "Success Command" to prove it works (e.g., `python --version`).

## 5. Documentation Checklist
- [ ] List specific package names for major distros.
- [ ] Identify if the tool requires a restart of the terminal.
- [ ] Provide the command to check the installed version.
