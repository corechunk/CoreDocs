# 🏷️ AST Type Checking Passes & Implicit Conversions

## 1. Type Resolution Pass
Semantic analysis traverses the AST to verify that operators and function calls receive arguments matching declared signatures (e.g., rejecting additions between strings and integers unless explicitly coerced).

## 2. Coercion Matrices & Promotion
Compilers define explicit coercion rules for widening implicit conversions (e.g., promoting a 32-bit `int` to a 64-bit `float`) while flagging narrowing conversions as compile-time errors.
