# 🏷️ Symbol Tables (.symtab) and Relocation Entries (.rela.text)

## 1. Symbol Tables (`.symtab`)
Contains metadata records mapping exported function and global variable strings to their exact byte offsets inside the `.text` or `.data` sections.

## 2. Relocation Entries (`.rela.text`)
When code references external library routines (e.g., `printf` or `malloc`) whose memory addresses are unknown at compile time, the AOT compiler writes **Relocation Entries**. The system dynamic linker (`ld-linux.so`) uses these entries at launch to patch target addresses directly into memory.
