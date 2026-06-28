# 📚 Dynamic Evaluation Environment Frames & Stack Allocation

## 1. Runtime Environment Frames
The interpreter tracks active runtime variable state using dynamic `Environment` structs holding key-value maps of symbol names to runtime values (`Value`).

## 2. Dynamic Scope Stacks
When entering block scopes or calling functions, the interpreter instantiates a new child environment frame linking to its parent scope environment, popping frames upon function return to free stack allocations.
