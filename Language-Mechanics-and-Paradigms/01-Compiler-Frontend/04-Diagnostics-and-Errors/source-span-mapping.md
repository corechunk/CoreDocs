# 📍 Source Span Mapping and Location Diagnostics

## 1. Source Spans
Every token and AST node retains a `Span` metadata object recording its precise location within the original source files:
- **Line Number**
- **Column Number**
- **Start & End Byte Offsets**

## 2. Professional Compiler Error Formatting
Source spans allow compilers (like Rustc or Clang) to print high-signal diagnostic snippets highlighting the exact code span responsible for compilation failures.
