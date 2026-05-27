# 🏛️ [Master Lua Reference (One-Shot)](master-lua.md)

# 🧭 Lua Language Blueprint: Tiered Learning (v2)

This roadmap groups the 53 universal language topics by **Mastery Tier**, targeting **Lua 5.4**.

---

## 🟢 Tier 1: The Foundation [CORE]
*The non-skippable essentials. Master these to write functional, correct Lua scripts.*

### Environment & Setup
- [01-toolchain-installation.md](./setup/01-toolchain-installation.md) (Lua 5.4, `hererocks`, `luarocks`)
- [02-compilation-run-basics.md](./setup/02-compilation-run-basics.md) (The `lua` interpreter, Bytecode `luac`, Hello World)

### Lexical & Data
- [03-tokens-lexemes.md](./04-tokens-lexemes.md) (Chunks, Blocks, and Identifiers)
- [04-keywords-standards.md](./05-keywords-standards.md) (Lua 5.1 -> 5.4 evolution)
- [05-comments-metadata.md](./07-comments-metadata.md) (Short/Long comments, EmmyLua `---@`)
- [06-variables-constants.md](./08-variables-constants.md) (`local`, `_G`, and `<const>`)
- [07-data-types.md](./09-data-types.md) (The 8 basic types Hub)
    - [numbers.md](./data-type/numbers.md) (Integers vs Floats)
    - [booleans.md](./data-type/booleans.md)
    - [nil.md](./data-type/nil.md)
    - [special-types.md](./data-type/special-types.md) (Userdata, Threads)
- [08-string-escaping.md](./10-string-escaping.md) (Hex, Decimal, and Unicode escapes)
- [09-interpolation.md](./11-interpolation.md) (String concatenation `..` vs `string.format`)
- [10-scope-lifetime.md](./12-scope-lifetime.md) (Lexical scoping, Upvalues)

### Logic & Control
- [11-operators.md](./17-operators.md) (Conceptual Hub)
    - [math.md](./operator/math.md)
    - [logical.md](./operator/logical.md) (and/or/not)
    - [bitwise.md](./operator/bitwise.md) (Lua 5.3+ natives)
    - [assignment.md](./operator/assignment.md)
- [12-precedence-associativity.md](./18-precedence-associativity.md)
- [13-expressions-statements.md](./19-expressions-statements.md)
- [14-type-casting.md](./21-type-casting.md) (Coercion vs `tonumber`/`tostring`)
- [15-truth-rule.md](./22-truth-rule.md) (Only `false` and `nil` are false)
- [16-conditionals.md](./23-conditionals.md) (Conceptual Hub)
    - [if-else.md](./control/if-else.md)
- [17-iteration-definite.md](./24-iteration-definite.md) (Numeric `for`, Generic `ipairs`)
- [18-iteration-indefinite.md](./25-iteration-indefinite.md) (`while`, `repeat..until`)

### The Function Engine
- [19-function-basics.md](./27-function-basics.md) (First-class values)
- [20-return-types.md](./28-return-types.md) (Multiple return values)
- [21-recursion.md](./29-recursion.md) (Tail-call optimization)
- [22-passing-mechanisms.md](./30-passing-mechanisms.md) (Value vs Table-Reference)

### Architecture & Environment
- [23-sequential-collections.md](./32-sequential-collections.md) (Tables as Arrays - 1-based)
    - [table-insert.md](./array/table-insert.md)
- [24-associative-collections.md](./33-associative-collections.md) (Tables as Hashmaps)
- [25-structs-base.md](./34-structs-base.md) (Tables as Records)
- [26-class-concept.md](./36-class-concept.md) (Metatable-based prototypes)
- [27-io-streams.md](./45-io-streams.md) (`io.read`, `io.write`, `print`)
- [28-error-handling.md](./49-error-handling.md) (`error`, `assert`, `pcall`, `xpcall`)

---

## 🔵 Tier 2: Idiomatic Power [PRO]
*Native techniques and efficiency. Master these to write "Professional" Lua.*

### Efficiency & Native Power
- [29-tuning-strictness.md](./06-tuning-strictness.md) (Enforcing `local`, strict.lua)
- [30-native-strings.md](./14-native-strings.md) (`string` library mastery)
- [31-pattern-matching.md](./15-pattern-matching.md) (Lua's unique pattern syntax)
- [32-command-substitution.md](./20-command-substitution.md) (`io.popen`)
- [33-jump-statements.md](./26-jump-statements.md) (`break`, `goto` [5.2+])
- [34-closures-lambdas.md](./31-closures-lambdas.md) (Lexical closures)

### Advanced Redirections
- [35-procedural-mechanisms.md](./procedural/35-procedural-mechanisms.md) (Hub)
    - [Modules & Require](./procedural/modules.md)
    - [Local-First Optimization](./procedural/locals.md)
- [36-advanced-oop.md](./oop/37-advanced-oop.md) (Metatables Hub)
    - [Encapsulation](./oop/encapsulation.md)
    - [Inheritance](./oop/inheritance.md)
    - [Polymorphism](./oop/polymorphism.md)
    - [Abstraction](./oop/abstraction.md)
- [37-async-coroutines.md](./concurrency/40-async-coroutines.md) (Coroutines Hub)
- [38-http-client-api.md](./network/44-http-client-api.md) (`luasocket`, `lua-http`)
- [39-redirection-piping.md](./46-redirection-piping.md) (CLI piping with Lua)

### Project Lifecycle & Build
- [40-multi-file-projects.md](./build/50-multi-file-projects.md) (`require`, `package.path`)
- [41-build-tools.md](./build/51-build-tools.md) (`luarocks` make, `amalg`)
- [42-standard-library.md](./53-standard-library.md) (Global environment reference)

---

## 🔴 Tier 3: Advanced Internals [SYSTEMS]
*The engine and the OS. Master these to build engines or C-modules.*

### Internals & Memory
- [43-charset.md](./03-charset.md) (Lua is 8-bit clean, UTF-8 library)
- [44-storage-classes.md](./13-storage-classes.md) (Registry, Upvalues, Environments)
- [45-syntactic-automation.md](./16-syntactic-automation.md) (Metatable `__index`, `__newindex` magic)
- [46-synchronization-locks.md](./concurrency/41-synchronization-locks.md) (Thread safety in C-modules)
- [47-exit-codes-signals.md](./47-exit-codes-signals.md) (`os.exit`, signal handling in C)
- [48-memory-management.md](./48-memory-management.md) (Garbage Collection internals)
    - [gc-cycles.md](./memory/gc-cycles.md)
    - [weak-tables.md](./memory/weak-tables.md)
- [49-pointer-mastery.md](./41-pointer-mastery.md) (Lightuserdata vs Full Userdata)

### Low-Level Concurrency
- [50-process-forking.md](./concurrency/38-process-forking.md) (via `luaposix`)
- [51-multi-threading.md](./concurrency/39-multi-threading.md) (`lanes`, `luv`, `lua-llthreads`)

### Low-Level Networking
- [52-socket-basics.md](./42-socket-basics.md) (`luasocket` core)
- [53-tcp-udp-patterns.md](./43-tcp-udp-patterns.md) (Select/Poll patterns)
