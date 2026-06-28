# 📦 Constructing Executable and Linkable Format (ELF) Binaries

## 1. ELF File Header Structures
AOT compilers generate standalone ELF binaries (or `.o` object files) by populating binary header structs defined in `<elf.h>` (`Elf64_Ehdr`).

## 2. Binary Section Layout
- **`.text` Section:** Holds compiled raw machine code execution bytes.
- **`.data` Section:** Holds initialized global variables.
- **`.bss` Section:** Holds uninitialized global variable reservations.
- **Program Headers (`Elf64_Phdr`):** Tells the OS kernel loader (`mmap`) which segments to map into virtual memory execution grids upon launching.
