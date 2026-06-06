# 📟 Terminal Physics: ANSI Escape Sequences

ANSI sequences are "In-Band" signaling bytes that control terminal behavior (color, cursor, screen).

## 1. Sequence Anatomy
A standard CSI (Control Sequence Introducer) looks like: `[38;2;R;G;Bm`

- `[` : The Escape Trigger (Octal: ``).
- `38` : Target Foreground (48 for Background).
- `2`  : Mode (TrueColor 24-bit).
- `R;G;B` : Values 0-255.
- `m`  : SGR Terminator (Select Graphic Rendition).

## 2. TrueColor Spectrum Math
To transition from Color A to Color B over a percentage (0-100):
`Current = Start + ((End - Start) * Percent / 100)`

## 3. High-Performance UI (60 FPS)
- **Raw Escapes**: Essential for speed. Avoid `tput` in loops to prevent fork overhead (~5ms/call).
- **
 (Carriage Return)**: Moves cursor to index 0 without a newline. Essential for loading bars.

---
*Relates to: [Bash Native Strings](../../../languages/bash/14-native-strings.md)*
