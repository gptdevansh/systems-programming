# Learning Timeline

This roadmap is designed to move from low-level C understanding into Rust systems programming with a strong conceptual foundation.

---

## Study Philosophy

Each month should include:

- concept study
- mini coding exercises
- debugging and tooling practice
- a small project or prototype
- a review of what you can explain plainly

---

## Month 1 — C Fundamentals

### Focus

- C basics
- memory model
- pointers
- arrays
- functions
- structs
- stack vs heap
- `malloc` / `free`

### Deliverables

- Recreate memory layout examples in C
- Write functions using pointers and arrays
- Explain stack vs heap with diagrams
- Build a small program using structs and dynamic memory

### Checkpoint

You should be able to explain:

- what a pointer stores
- what memory layout looks like in a function call
- how arrays decay into pointers
- how `malloc` changes lifetime

---

## Month 2 — Systems and Debugging

### Focus

- memory bugs
- undefined behavior
- compilation pipeline
- assembly basics
- GDB
- processes
- system calls

### Deliverables

- Debug a memory bug with sanitizers
- Use GDB to inspect stack frames and variables
- Trace a simple process lifecycle with `fork` / `exec`
- Write a tiny program that exposes UB and explain why it happens

### Checkpoint

You should be able to explain:

- why UB is a compiler contract issue, not just a bug
- how the compiler, linker, and loader fit together
- what happens when a program calls into the kernel
- how a process differs from a program

---

## Transition: Start Rust

```text
        ↓
   🦀 START RUST
        ↓
```

### Rust transition goal

By the end of Month 2, you should be ready to study Rust with a clear understanding of why safety and ownership exist.

---

## Month 3 — Rust Fundamentals

### Focus

- Rust fundamentals
- Cargo
- ownership
- borrowing
- references
- structs
- enums
- pattern matching
- error handling

### Deliverables

- Build small CLI apps with Cargo
- Write code that demonstrates borrowing and ownership
- Reimplement a small C-like program in Rust
- Practice `Result`, `Option`, and pattern matching

### Checkpoint

You should be able to explain:

- why ownership exists
- the difference between move, borrow, and reference
- what the borrow checker is enforcing
- how enums and pattern matching model state

---

## Month 4 — Rust Deeper Concepts

### Focus

- lifetimes
- traits
- generics
- collections
- iterators
- smart pointers
- concurrency

### Deliverables

- Implement a small generic data structure
- Use iterators and collections effectively
- Build a small multi-threaded Rust program
- Explain lifetimes in plain language

### Checkpoint

You should be able to explain:

- why lifetimes matter
- how traits enable abstraction
- how ownership interacts with concurrency
- what smart pointers are doing beneath the hood

---

## Month 5+ — Serious Systems Rust

### Focus

- networking
- async
- Tokio
- databases
- operating systems
- compilers
- distributed systems

### Deliverables

- Build a small TCP server/client
- Use async tasks for I/O-heavy workloads
- Connect to a simple database or local service
- Explore one systems topic deeply with a mini project

### Checkpoint

You should be able to explain:

- how I/O and concurrency fit together in async systems
- how a simple server handles multiple clients
- where Rust helps and where OS abstractions still matter

---

## Practical Project Ladder

Build these progressively:

1. Memory playground in C
2. Pointer and struct exercises in C
3. Debugging lab using sanitizers and GDB
4. Small Rust CLI app
5. Threaded Rust service or mini server
6. Async networking toy project

---

## Overall Goal

Build the mental model needed to reason about:

- memory layout
- ownership and lifetime
- hardware and OS boundaries
- safe concurrency
- systems-level design
- performance and correctness tradeoffs

> The progression is intentional: understand C deeply before moving into Rust and advanced systems work.