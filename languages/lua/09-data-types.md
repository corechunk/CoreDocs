# 09 - Data Types (CORE - Hub)

Definition: Lua is a dynamically typed language, meaning variables do not have types; only values do. There are eight basic types in Lua: `nil`, `boolean`, `number`, `string`, `function`, `userdata`, `thread`, and `table`.

## Type System Overview

| Type | Description | Link |
| :--- | :--- | :--- |
| **Nil** | Represents the absence of a value. | [nil](./data-type/nil.md) |
| **Boolean** | `true` or `false`. Only `false` and `nil` are falsy. | [booleans](./data-type/booleans.md) |
| **Number** | Real (double-precision floating-point) numbers and Integers (since 5.3). | [numbers](./data-type/numbers.md) |
| **String** | Immutable sequences of bytes. | [10-string-escaping](./10-string-escaping.md) |
| **Function** | First-class citizens in Lua. | [27-function-basics](./27-function-basics.md) |
| **Table** | The only data structuring mechanism; associative arrays. | [32-sequential-collections](./32-sequential-collections.md) |
| **Userdata** | Allows arbitrary C data to be stored in Lua variables. | [special-types](./data-type/special-types.md) |
| **Thread** | Represents independent lines of execution (coroutines). | [special-types](./data-type/special-types.md) |

# The Logic Bridge
Understanding types in Lua is fundamental because the language uses them to determine behavior via metatables. While Lua is dynamic, 5.3+ introduced a subtype distinction for `number` (integer vs float) which is critical for performance and bitwise operations.
