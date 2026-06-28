# 🏛️ Base Language Syntax & Systems Knowledge Requirement

This document formalizes the exact language syntax coverage and low-level systems knowledge required to build a hybrid language engine, categorizing what is mandatory for the Base Core Engine vs. Advanced Extensions.

---

## 🗺️ Language Base Syntax Coverage Requirements

### 1. Mandatory Core Syntax (Base Engine v1.0)
* **Variable Declarations & Types:** Understanding `var` (mutable), `val` (immutable), explicit type annotations (`int`, `float`, `string`, `bool`), and basic type inferencing.
* **Control Flow Primitives:** Conditionals (`if`/`else`), loops (`while`/`for`), and return statements (`return`).
* **Functions & Scope:** Function declarations, parameter passing mechanisms (pass-by-value vs pass-by-reference), recursion, and lexical block scoping (`{ ... }`).
* **Memory Data Layouts (Structs):** C-style `struct` definitions (plain data containers) and contiguous arrays/lists.

### 2. OOP & Class Boundaries (Separate Advanced Module)
* **Base Core Bound:** Stop at `struct` containers for Base v1.0 to keep performance optimal and avoid vtable overhead.
* **Advanced Extension Bounds:** Classes, single/multiple inheritance, encapsulation (`public`/`private`), virtual method tables (`vtables`), and interface implementations should be separated into Phase 02/04 runtime extensions.

---

## ⚙️ Systems & Execution Knowledge Requirements

### 1. Concurrency Primitives Coverage
* **Process Level (`fork`/`exec`):** Understanding Unix process boundaries, process IDs (`PID`), process groups, job control, and backgrounding (`&`).
* **Thread Level (`pthreads`/C11 threads):** Shared memory models, thread allocation, race conditions, atomic operations, and mutex locks.
* **Asynchronous / Event-Loop Level:** Non-blocking event loops, coroutines (`async`/`await` state machines), and non-blocking I/O multiplexing (`epoll`/`select`).

### 2. Network & Socket Handling Coverage
* **Raw Socket Physics:** C socket API (`socket()`, `bind()`, `listen()`, `accept()`, `connect()`).
* **Protocol Stacks:** Stream semantics (TCP) vs Datagrams (UDP), IPv4/IPv6 addressing, port bindings, and buffer byte order conversions (`htons`/`htonl`).
* **High-Level Networking:** Parsing HTTP/HTTPS text headers and serialization formatting (JSON / MessagePack).

---

## 💡 Data Structures Mapping to Compiler Tasks

* **Stacks:** Used for AST operator precedence parsing (Shunting-yard algorithm) and tracking active call stack frames in interpreters.
* **Queues:** Used for streaming Lexer tokens to the Parser and managing asynchronous event loops.
* **Hash Tables (Symbol Tables):** Used for resolving variables, functions, and struct fields within nested lexical scopes.
* **Trees (AST):** Used to represent program structures in memory for recursive evaluation.

---

## 🛠️ Required Knowledge Depth Per Development Phase

```text
┌─────────────────────────────────────────────────────────────────────────┐
│ PHASE 00: Language & Grammar Design                                     │
│ Required Coverage: Variables, Functions, Structs, Control Flow Syntax.  │
│ Focus: EBNF grammar, token definitions, operator precedence.            │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│ PHASE 01: Interactive Shell & Lexer/Parser Front-End                    │
│ Required Coverage: Linear DS (Stacks/Queues) & POSIX process primitives.│
│ Focus: Tokenizing text, AST nodes, fork/exec command execution loop.    │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│ PHASE 02: Scripting Interpreter & Standard Library                      │
│ Required Coverage: Hash Maps, Struct memory, Socket I/O APIs.           │
│ Focus: AST evaluation, scope stack frames, stdlib system bindings.     │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│ PHASE 03: JIT Compiler Engine                                           │
│ Required Coverage: Virtual memory (mmap PROT_EXEC), x86/ARM Opcodes.    │
│ Focus: Hotspot profiling counters, dynamic machine code emission.      │
└────────────────────────────────────┬────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│ PHASE 04: Native Ahead-Of-Time (AOT) Static Compiler                   │
│ Required Coverage: Target ISA Calling Conventions (ABI), ELF Spec.      │
│ Focus: Register allocation algorithms, writing binary executable headers.│
└─────────────────────────────────────────────────────────────────────────┘
```
