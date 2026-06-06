# 🖥️ Windows Terminal Compatibility

## 1. Legacy Console (conhost.exe)
- Found in Windows 7, 8, and early 10.
- **Limited Colors**: Supports only 16 colors. TrueColor (`\e[38;2;...`) will show as raw text.

## 2. Modern Windows Terminal
- Supports TrueColor, Unicode symbols (like `█`), and GPU acceleration.
- **Environment Variable**: Use `$COLUMNS` for width, as it is more reliable than `tput cols` in this environment.
