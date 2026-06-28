# 🔄 Parameter Passing Semantics

## 1. Evaluation Strategies
- **Eager Evaluation:** Arguments are evaluated before control enters the called function.
- **Lazy Evaluation:** Arguments are deferred until their evaluated values are explicitly accessed.

## 2. Parameter Passing Modes
- **Pass-by-Value:** Function receives a copied instance of the data payload.
- **Pass-by-Reference:** Function receives direct access to the caller's memory address space.
- **Pass-by-Sharing:** Function receives a copied reference pointer pointing to shared dynamic heap objects.
