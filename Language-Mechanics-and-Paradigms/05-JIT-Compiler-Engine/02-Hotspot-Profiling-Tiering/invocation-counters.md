# 🔥 Invocation Counters and Hotspot Detection

## 1. Hotspot Identification
Compiling every bytecode instruction to native machine code introduces compilation latency overhead. JIT engines only compile "hotspots"—functions or loops executed frequently.

## 2. Invocation Counter Thresholds
The runtime VM increments execution counters on function entries and back-edges of loops. When a counter exceeds a designated threshold, the runtime triggers dynamic compilation.
