# 🗄️ Symbol Tables and Stack Frames

## 1. Symbol Table Data Structure
Compilers and interpreters track active symbols using nested **Hash Tables**. Each lexical scope level maintains a dictionary mapping identifier strings to type definitions and memory offsets.

## 2. Scope Chaining
When resolving a variable name, the lookup algorithm checks the current scope's symbol table first, recursively traversing parent pointers up to the global scope table.
