# ⚡ Terminal Dynamics & High-Speed UI

This file notes the performance constraints and solutions for building modern, high-speed terminal interfaces.

## 1. 60 FPS Timing
To achieve smooth animations (like loading bars), the interface must redraw every **16.6ms**.

- **Interval**: `sleep 0.016`
- **Constraint**: **Zero Process Forks**. In a 60 FPS loop, you cannot call external commands like `tput`, `ls`, or `wc`. They take ~5-10ms to start, which will lag the UI.

## 2. Fast State Counting (The "Pure Bash" Way)
Instead of `ls | wc -l`, use **Glob Expansion** and **Arrays** to count files in memory.

```bash
# FAST: Stays inside shell memory
files=( "$tmp_dir"/*.done )
count="${#files[@]}"

# Handling empty glob results
[[ -e "${files[0]}" ]] || count=0
```

## 3. Terminal Dimensions
- **$COLUMNS**: A built-in shell variable that updates automatically. Use this instead of `tput cols` for instant access.

## 4. Builtins vs Externals
- **Builtin**: Functions compiled into the `bash` binary (e.g., `printf`, `read`). No fork required.
- **External**: Programs on the disk (e.g., `/usr/bin/git`). Requires OS fork.
- **Verification**: Run `type <command>` to check.

---
*Relates to: [ANSI Escapes](./ANSI-Escapes.md)*
