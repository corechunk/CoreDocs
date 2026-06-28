# 🔄 Opcode Dispatch Loops: Switch vs. Direct-Threaded Code

## 1. Standard Switch-Dispatch Loops
The central VM execution engine loops over bytecode arrays, executing opcodes inside a monolithic `switch(ip++)` statement.

## 2. Direct-Threaded Code Optimization
To eliminate branch misprediction penalties associated with monolithic `switch` statements, production VMs (like LuaJIT or Python 3.12+) use **Direct-Threaded Code** (using GCC `&&label` jump tables) to jump directly from the tail of one opcode implementation into the next.
