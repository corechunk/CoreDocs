<!--
PROMPT CONTEXT:
"so now we will make c++ wiki with legacy aware annotation for what we would do in legacy code in another code snippet like having to add header for bool also 

thats it but before making the wiki i want you to read the whole pseudo-language/ folder and all files in it thoroughly. then ull confirm and present what u understood then ill permit to procceed"

"also u must make v1 and v2 file like

overview.md and overview-v2.md then after making all the 53 files u have to make a master-cpp.md with master blueprint

and those 53 files, some of them are core pro and sytem each will follow their own blueprints. also i dont have to remind you that u must use code snippets. dont try to glove every topic in one file to be globed in one code box but for saperate things or saperate implimentation in a file use another saperate code box.
-->

# 🏛️ [Master C++ Reference (One-Shot)](master-cpp.md)

# 🧭 C++ Language Blueprint: The Full Picture

This is the **Chronological Path**. Topics are ordered by the natural learning progression, with status tags to indicate their level.

---

## 🗺️ The Roadmap

### Phase 1: Environment & Setup
1. [01-toolchain-installation.md](./setup/01-toolchain-installation.md) **[CORE]** (OS-specific setup, `mise`, PATH)
2. [02-compilation-run-basics.md](./setup/02-compilation-run-basics.md) **[CORE]** (Execution ritual, Hello World)

### Phase 2: Lexical Foundations
3. [03-charset.md](./03-charset.md) **[SYSTEMS]** (UTF-8, Unicode, String Literals)
4. [04-tokens-lexemes.md](./04-tokens-lexemes.md) **[CORE]** (Atoms of the language)
5. [05-keywords-standards.md](./05-keywords-standards.md) **[CORE]** (Evolution C++98 to C++23)
6. [06-tuning-strictness.md](./06-tuning-strictness.md) **[PRO]** (Warnings, Sanitizers, Modern flags)
7. [07-comments-metadata.md](./07-comments-metadata.md) **[CORE]** (Doxygen, Attributes)

### Phase 3: Primitive Data
8. [08-variables-constants.md](./08-variables-constants.md) **[CORE]** (Initialization, `constexpr`)
9. [09-data-types.md](./09-data-types.md) **[CORE]** (Conceptual Hub)
    - [integers.md](./data-type/integers.md)
    - [floats.md](./data-type/floats.md)
    - [fixed-width.md](./data-type/fixed-width.md)
    - [special-types.md](./data-type/special-types.md)
10. [10-string-escaping.md](./10-string-escaping.md) **[CORE]** (Raw strings, Escape sequences)
11. [11-interpolation.md](./11-interpolation.md) **[CORE]** (std::format, iostreams)
12. [12-scope-lifetime.md](./12-scope-lifetime.md) **[CORE]** (RAII, Namespaces)
13. [13-storage-classes.md](./13-storage-classes.md) **[SYSTEMS]** (Static, Thread_local, Extern)

### Phase 4: Native Power (Efficiency)
14. [14-native-strings.md](./14-native-strings.md) **[PRO]** (std::string, std::string_view)
15. [15-pattern-matching.md](./15-pattern-matching.md) **[PRO]** (std::regex)
16. [16-syntactic-automation.md](./16-syntactic-automation.md) **[SYSTEMS]** (Templates, Concepts, Type-traits)

### Phase 5: Operations & Logic
17. [17-operators.md](./17-operators.md) **[CORE]** (Conceptual Hub)
    - [math.md](./operator/math.md)
    - [logical.md](./operator/logical.md)
    - [bitwise.md](./operator/bitwise.md)
    - [assignment.md](./operator/assignment.md)
18. [18-precedence-associativity.md](./18-precedence-associativity.md) **[CORE]** (Order of operations)
19. [19-expressions-statements.md](./19-expressions-statements.md) **[CORE]** (lvalues, rvalues, statements)
20. [20-command-substitution.md](./20-command-substitution.md) **[PRO]** (std::system, popen)
21. [21-type-casting.md](./21-type-casting.md) **[CORE]** (static_cast, dynamic_cast)

### Phase 6: Control Flow
22. [22-truth-rule.md](./22-truth-rule.md) **[CORE]** (Truthiness, std::boolalpha)
23. [23-conditionals.md](./23-conditionals.md) **[CORE]** (Conceptual Hub)
    - [if-else.md](./control/if-else.md)
    - [switch.md](./control/switch.md)
24. [24-iteration-definite.md](./24-iteration-definite.md) **[CORE]** (Range-based for)
25. [25-iteration-indefinite.md](./25-iteration-indefinite.md) **[CORE]** (While, Do-While)
26. [26-jump-statements.md](./26-jump-statements.md) **[PRO]** (Break, Continue, Goto)

### Phase 7: The Function Engine
27. [27-function-basics.md](./27-function-basics.md) **[CORE]** (Overloading, Default args)
28. [28-return-types.md](./28-return-types.md) **[CORE]** (auto, trailing return)
29. [29-recursion.md](./29-recursion.md) **[CORE]** (Tail recursion optimization)
30. [30-passing-mechanisms.md](./30-passing-mechanisms.md) **[CORE]** (Reference, Move, Value)
31. [31-closures-lambdas.md](./31-closures-lambdas.md) **[PRO]** (Lambdas, Capture lists)

### Phase 8: Procedural Architecture
32. [32-sequential-collections.md](./32-sequential-collections.md) **[CORE]** (Conceptual Hub)
    - [fixed.md](./array/fixed.md)
    - [vla.md](./array/vla.md)
    - [multidim.md](./array/multidim.md)
33. [33-associative-collections.md](./33-associative-collections.md) **[CORE]** (std::map, std::unordered_map)
34. [34-structs-base.md](./34-structs-base.md) **[CORE]** (POD types, Aggregates)
35. [35-procedural-mechanisms.md](./procedural/35-procedural-mechanisms.md) **[PRO]**
    - Namespaces, Tuples, Optional.

### Phase 9: Object-Oriented Programming
36. [36-class-concept.md](./36-class-concept.md) **[CORE]** (Encapsulation, Constructors)
37. [37-advanced-oop.md](./oop/37-advanced-oop.md) **[PRO]** (Hub)
    - [Encapsulation](./oop/encapsulation.md)
    - [Inheritance](./oop/inheritance.md)
    - [Polymorphism](./oop/polymorphism.md)
    - [Abstraction](./oop/abstraction.md)

### Phase 10: Concurrency & Async
38. [38-process-forking.md](./38-process-forking.md) **[SYSTEMS]** (Conceptual Hub)
    - [fork.md](./concurrency/fork.md)
    - [exec.md](./concurrency/exec.md)
39. [39-multi-threading.md](./concurrency/39-multi-threading.md) **[SYSTEMS]** (std::thread, std::jthread)
40. [40-async-coroutines.md](./concurrency/40-async-coroutines.md) **[PRO]** (std::async, Coroutines)
41. [41-synchronization-locks.md](./concurrency/41-synchronization-locks.md) **[SYSTEMS]** (std::mutex, std::atomic)

### Phase 11: Network Handling
42. [42-socket-basics.md](./42-socket-basics.md) **[SYSTEMS]** (Conceptual Hub)
    - [listen.md](./network/listen.md)
    - [connect.md](./network/connect.md)
43. [43-tcp-udp-patterns.md](./network/43-tcp-udp-patterns.md) **[SYSTEMS]** (Boost.Asio basics)
44. [44-http-client-api.md](./network/44-http-client-api.md) **[PRO]** (CPR, libcurl++)

### Phase 12: OS Bridge & Memory
45. [45-io-streams.md](./45-io-streams.md) **[CORE]** (std::cin, std::cout, std::cerr)
46. [46-redirection-piping.md](./46-redirection-piping.md) **[PRO]** (File streams, Buffer redirection)
47. [47-exit-codes-signals.md](./47-exit-codes-signals.md) **[SYSTEMS]** (Process lifecycle)
48. [48-memory-management.md](./48-memory-management.md) **[SYSTEMS]** (Conceptual Hub)
    - [stack-heap.md](./memory/stack-heap.md)
    - [allocation.md](./memory/allocation.md)
    - [pointer-arithmetic.md](./memory/pointer-arithmetic.md)
49. [49-error-handling.md](./49-error-handling.md) **[CORE]** (Exceptions, std::expected)

### Phase 13: Project Lifecycle & Build
50. [50-multi-file-projects.md](./build/50-multi-file-projects.md) **[PRO]**
    - Modules, Headers, Linking.
51. [51-build-tools.md](./build/51-build-tools.md) **[PRO]**
    - CMake, Ninja, Make.
52. [52-linking-delivery.md](./build/52-linking-delivery.md) **[SYSTEMS]**
    - Shared vs Static libraries.
53. [53-standard-library.md](./build/53-standard-library.md) **[PRO]** (STL, Boost list)

---

## 🏷️ Tier Definitions
- **[CORE]**: Fundamental logic. Essential for beginners.
- **[PRO]**: Native power and idiomatic efficiency.
- **[SYSTEMS]**: Low-level internals and OS integration.
