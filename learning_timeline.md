# Learning Timeline

A phase-based overview of the journey from C fundamentals to serious systems Rust. Use this alongside `phase-1-c-fundamentals.md` for the detailed chapter map.

**Important:** This timeline shows approximate phases, not fixed calendar deadlines. Advancement is always based on Gate 2 mastery — not on time spent. Some phases may take longer. That is correct behavior, not a problem.

---

## Study Philosophy

Each phase should include:

- concept study (deep, not surface)
- small C or Rust experiments
- debugging and tooling practice
- at least one mandatory milestone project
- a review of what you can explain in plain language without notes

---

## Phase 1 — C Foundation (Chapters 0–11)

**Goal:** Build the mental model required to enter Rust.

### Topics

- Mental model of programs and hardware
- C fundamentals: types, variables, control flow, functions
- Memory: bits, addresses, stack, heap, allocation, lifetime, ownership concept
- Pointers: deeply — this is the single most important chapter before Rust
- Arrays, strings, and the array/pointer relationship
- Functions and the calling mechanism
- Structs, unions, enums
- Type system
- Compilation pipeline: C → preprocessor → assembly → object → linker → ELF
- Assembly and machine-level understanding, including computer architecture
- Undefined behavior
- Storage duration and lifetime

### Milestone Projects

| Project | When |
|---|---|
| Dynamic array (`malloc`/`free` manually) | After Ch 2–3 |
| Hash table with chaining | After Ch 4–6 |
| `objdump` / `readelf` analysis of your own binary | After Ch 8–9 |

### Gate Criteria

Before exiting Phase 1, you must be able to:

- explain how a program is laid out in memory
- explain what a pointer holds and what dereferencing does
- reason about lifetime: why a value dies, when memory is freed
- explain what undefined behavior is and why the compiler can exploit it
- describe compilation from source to executable
- read a simplified disassembly and match it to C
- identify common memory bugs and explain why they are dangerous

---

## 🦀 Rust Entry Gate

Enter Rust after passing the Phase 1 gate — not after a fixed number of weeks.

---

## Phase 2 — Rust Fundamentals + C in Parallel (Chapters 12–20)

**Goal:** Learn Rust with C as the comparison lens. Study C systems topics alongside Rust.

### Rust topics

- Cargo and project structure
- Ownership, borrowing, references
- Move semantics
- Structs and enums
- Pattern matching
- Error handling (`Result`, `Option`)
- Traits and generics
- Iterators and collections
- Smart pointers (`Box`, `Rc`, `Arc`, `RefCell`)
- Lifetimes
- Closures

### C / Systems topics (parallel)

- Linkage and visibility
- Build systems
- File I/O and OS interface
- Processes (`fork`, `exec`, signals, pipes)
- Threads, mutex, condition variables, atomics
- Virtual memory
- System calls
- Networking: TCP/IP, UDP, DNS, HTTP, sockets, epoll

### Milestone Projects

| Project | When |
|---|---|
| `cat` clone using only system calls | After Ch 14–15 |
| Mini shell (`fork`/`exec`/`wait`) | After Ch 15 |
| Thread pool | After Ch 16 |
| TCP echo server | After Ch 19 |
| HTTP/1.1 server (non-blocking, epoll) | After Ch 19 |
| Rebuild dynamic array and hash table in Rust | After Rust fundamentals |

### Checkpoint

You should be able to:

- explain why Rust ownership exists by pointing to a real C memory bug
- explain the difference between move, borrow, and reference
- explain what the borrow checker is enforcing and why
- build a multi-threaded program in both C and Rust
- trace a complete networking request from socket to epoll to handler

---

## Phase 3 — Advanced Systems (Chapters 21–27)

**Goal:** Deepen systems knowledge; tackle the hardest topics.

### Topics

- Memory allocator (build your own `malloc`)
- Debugging and observability at depth (GDB, perf, core dumps)
- Security: buffer overflow, stack smashing, use-after-free, ASLR, NX, canaries
- C standard library internals
- ABI and FFI: how C and Rust interoperate at the binary level
- Hardware interaction: memory-mapped I/O, interrupts, DMA, embedded C
- Advanced C: variadic functions, `setjmp`/`longjmp`, `_Atomic`, `_Generic`

### Milestone Projects

| Project | When |
|---|---|
| Memory allocator (`malloc` reimplemented) | Ch 21 |
| C-to-Rust FFI binding using `bindgen` | Ch 25 |

### Checkpoint

You should be able to:

- implement a working memory allocator from scratch
- explain how `extern "C"` enables Rust to call a C library
- explain ASLR and how it relates to pointer values at runtime
- write an embedded-style program using volatile and memory-mapped registers

---

## Phase 4 — Serious Systems Rust

**Goal:** Apply everything to real systems engineering.

### Topics

- Async Rust (Tokio, futures, executors)
- Networking at scale (async TCP, HTTP, TLS)
- Databases (query engines, storage, transactions)
- Operating systems internals
- Compilers and runtimes
- Distributed systems
- Performance engineering

### Milestone Projects

| Project | Description |
|---|---|
| Async TCP chat server | Multiple clients, async I/O, Tokio |
| Simple HTTP server | Request parsing, routing, responses |
| Key-value store | Persistence, concurrent access |
| Mini shell in Rust | Rebuild the C shell project |

---

## Practical Project Ladder (Full Sequence)

```
Dynamic array (C)
    ↓
Hash table (C)
    ↓
Binary analysis (objdump / readelf)
    ↓
cat clone (C, syscalls only)
    ↓
Mini shell (C)
    ↓
Thread pool (C)
    ↓
TCP echo server (C)
    ↓
HTTP server (C, epoll)
    ↓
Memory allocator (C)
    ↓
Rebuild: dynamic array + hash table (Rust)
    ↓
FFI binding (C library → Rust)
    ↓
Async TCP server (Rust, Tokio)
    ↓
Key-value store (Rust)
```

---

## Overall Goal

Build the mental model needed to reason independently about:

- memory layout and ownership
- hardware and OS boundaries
- safe concurrency
- systems-level design
- performance and correctness tradeoffs

> The structure is intentional: the C foundation reveals the problems. Rust provides the solutions. Systems knowledge makes both meaningful.
