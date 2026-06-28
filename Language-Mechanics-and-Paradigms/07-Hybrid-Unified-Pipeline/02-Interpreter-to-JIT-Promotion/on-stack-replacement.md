# 🔄 On-Stack Replacement (OSR) Mechanics

## 1. Dynamic Loop Promotion
When an interpreted bytecode loop invocation counter hits a hotspot threshold, waiting for the function to return before calling a JIT version wastes execution time.

## 2. On-Stack Replacement (OSR) Execution
OSR compiles the hot loop body to JIT RAM memory dynamically, rewrites active interpreter stack frames into native machine frame alignments, and jumps directly into compiled machine code mid-execution.
