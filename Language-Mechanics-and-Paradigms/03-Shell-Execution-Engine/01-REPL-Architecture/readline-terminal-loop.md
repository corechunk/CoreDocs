# 🖥️ Readline Terminal Loops & Raw Mode

## 1. Terminal Cooked vs. Raw Mode
By default, Unix terminals operate in cooked mode (buffering input lines until Enter is pressed). Interactive shells switch the TTY terminal descriptor to raw mode (`termios` flags) to process keystrokes individually in real time.

## 2. Multi-Line Buffer Assembly
When users input multi-line constructs (e.g., unclosed braces or loop blocks), the REPL loop alters the prompt indicator (from `>` to `...`) and accumulates character streams into dynamic heap memory buffers until block evaluation criteria are met.
