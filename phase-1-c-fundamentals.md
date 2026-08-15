# Phase 1: C Fundamentals & Systems Foundation

This file is the core study map for the systems programming roadmap. The goal is not just to learn C — it is to build a deep mental model of hardware, memory, compilation, and OS interaction that will make Rust ownership, lifetimes, and concurrency feel inevitable rather than arbitrary.

---

## Structure of This Phase

This roadmap is **not a single linear prerequisite chain**. It is layered:

```
CHAPTERS 0–11 → Rust Entry Gate
                     │
              🦀 Rust Begins
                     │
CHAPTERS 12–20 → Run in parallel with Rust
                     │
CHAPTERS 21–27 → Advanced Systems (after Rust is comfortable)
```

Do not wait until chapter 27 before touching Rust. That is prerequisite hell.

---

## 🦀 Rust Entry Gate

You are ready to start Rust when you have completed chapters 0–11 with genuine understanding. The gate is not about finishing — it is about whether you can reason independently about memory, pointers, lifetime, undefined behavior, and the machine model.

**Gate criteria — before starting Rust, you must be able to:**

- explain how a program is laid out in memory (stack, heap, code, data)
- explain what a pointer actually holds and what dereferencing does
- reason about lifetime: why a value dies, when memory is freed
- explain what undefined behavior is and why the compiler can exploit it
- describe what happens when C is compiled, from source to executable
- read a simplified disassembly and match it to the original C
- identify common memory bugs and explain why they are dangerous

---

## How to Study Each Topic

Treat every topic as a conceptual foundation, not a reading list.

### Study loop

1. Read the concept
2. Write a small C example
3. Run it and observe the behavior
4. Debug it using compiler warnings, GDB, or sanitizers
5. Re-explain the concept in plain language without looking at notes

### Gate 1 / Gate 2

Every topic follows the full lesson protocol defined in `system-prompt.md`.

---

## Milestone Projects

Projects are mandatory checkpoints, not optional exercises. Complete each one before advancing past its chapter group.

| After | Project | Concepts exercised |
|---|---|---|
| Ch 2–3 | Dynamic array (manual `malloc`/`free`) | Heap, pointers, ownership |
| Ch 4–6 | Hash table with chaining | Structs, linked lists, pointer-to-struct |
| Ch 8–9 | `objdump` / `readelf` analysis of your own binary | Compilation, ELF, linking, assembly |
| Ch 14–15 | `cat` clone using only system calls | File I/O, system calls |
| Ch 15 | Mini shell (`fork`/`exec`/`wait`) | Processes, pipes, signals |
| Ch 16 | Thread pool | Threads, mutex, condition variables |
| Ch 19 | TCP echo server | Sockets, blocking I/O |
| Ch 19 | HTTP/1.1 server | Non-blocking I/O, epoll, concurrency |
| Ch 21 | Memory allocator (`malloc` reimplemented) | Allocator internals, alignment, free lists |
| Rust begins | Rebuild dynamic array and hash table in Rust | Compare ownership, lifetimes, safety |

---

# REQUIRED BEFORE RUST — Chapters 0–11

---

## 0. Mental Model — Before C

### 0.1 What Is a Program?

- Source code
- Executable
- Instructions
- Data
- State
- Input / output

### 0.2 What Is a Computer?

- CPU
- Memory
- Storage
- I/O
- Bus
- Devices

### 0.3 Hardware vs Software

- Hardware
- Firmware
- Operating system
- Runtime
- Application

### 0.4 Abstraction Layers

```
Hardware
  ↓
Machine code
  ↓
Assembly
  ↓
C
  ↓
Libraries / OS
  ↓
Application
```

### 0.5 What Actually Happens When Code Runs?

- Load
- Decode
- Execute
- Memory access
- Register operations
- Branching
- Function calls

---

## 1. C Language Fundamentals

### 1.1 C's Philosophy

- Low-level control
- Minimal runtime
- Manual resource management
- Compilation model
- Undefined behavior
- Portability

### 1.2 Program Structure

- `main`
- Statements
- Expressions
- Blocks
- Scope
- Translation units

### 1.3 Types

- `char`, `short`, `int`, `long`, `long long`
- `float`, `double`
- `_Bool`
- `void`

### 1.4 Type Properties

- Size
- Alignment
- Representation
- Signedness
- Range
- Precision

### 1.5 Constants

- Integer literals
- Floating literals
- Character constants
- String literals
- Hexadecimal / octal / binary

### 1.6 Variables

- Declaration
- Definition
- Initialization
- Assignment
- Lifetime
- Scope
- Storage duration

### 1.7 Operators

- Arithmetic
- Relational
- Logical
- Bitwise
- Assignment
- Increment / decrement
- Conditional
- `sizeof`
- Cast

### 1.8 Control Flow

- `if` / `else`
- `switch`
- `for` / `while` / `do while`
- `break` / `continue`
- `goto`

---

## 2. Memory — ⭐⭐⭐⭐⭐

This is the most important chapter in the entire roadmap. Do not rush it.

### 2.1 Memory Fundamentals

- Bits
- Bytes
- Addresses
- Address space
- Memory cells

### 2.2 Data Representation

- Binary
- Hexadecimal
- Decimal
- Two's complement (signed integers)
- Integer overflow behavior
- IEEE 754 (floating point)
- Character encoding (ASCII)

### 2.3 Endianness ⭐

- Big-endian
- Little-endian
- Why it matters: networking, files, binary formats
- How to detect endianness in C
- Byte-swapping

> This is critical for networking and any binary protocol work.

### 2.4 Memory Layout

```
High addresses
  ┌──────────────┐
  │    Stack     │  ← grows downward
  ├──────────────┤
  │     ↓        │
  │              │
  │     ↑        │
  ├──────────────┤
  │    Heap      │  ← grows upward
  ├──────────────┤
  │     BSS      │  (uninitialized globals)
  ├──────────────┤
  │    Data      │  (initialized globals)
  ├──────────────┤
  │    Text      │  (code / read-only)
  └──────────────┘
Low addresses
```

### 2.5 Stack

- Stack frame
- Stack pointer
- Frame pointer
- Local variables
- Return address
- Function arguments
- Stack growth direction
- Stack overflow

### 2.6 Heap

- Dynamic allocation
- Allocation metadata
- Fragmentation (internal / external)
- Allocation lifetime
- Deallocation

### 2.7 C Allocation

- `malloc` / `calloc` / `realloc` / `free`
- What `malloc` actually returns
- What happens when allocation fails
- Alignment of returned memory

### 2.8 Memory Ownership

- Who allocated?
- Who owns?
- Who may access?
- Who may modify?
- Who releases?

> This mental model is the direct foundation for Rust's ownership system.

### 2.9 Memory Errors

- Memory leak
- Double free
- Use-after-free
- Dangling pointer
- Buffer overflow / out-of-bounds access
- Uninitialized memory read
- Invalid free
- Heap corruption
- Stack corruption

### 2.10 Memory Debugging Tools

- Valgrind
- AddressSanitizer (ASan)
- UndefinedBehaviorSanitizer (UBSan)
- GDB memory inspection

---

## 3. Pointers — ⭐⭐⭐⭐⭐

Do not rush this chapter. It is your most important prerequisite for Rust.

### 3.1 Pointer Fundamentals

- What a pointer contains (an address)
- Pointer variable declaration
- Address-of operator (`&`)
- Dereference operator (`*`)
- Pointer types and what the type means

### 3.2 Pointer Arithmetic

- Increment / decrement
- Addition / subtraction
- Pointer difference
- How type size affects arithmetic

### 3.3 Pointer Relationships

- Pointer → value
- Pointer → pointer (`**`)
- Pointer → array
- Pointer → struct
- Pointer → function

### 3.4 Pointer Type Variants

- `void *`
- `char *`
- `const T *` (pointer to const)
- `T *const` (const pointer)
- `const T *const` (both)

### 3.5 Pointer Safety

- Null pointer
- Dangling pointer
- Wild pointer (uninitialized)
- Invalid pointer (freed or out of bounds)
- Pointer lifetime and the object it points to

### 3.6 Function Pointers

- Function address
- Callback pattern
- Dispatch tables
- Arrays of function pointers

### 3.7 Advanced Pointers

- Pointer-to-pointer
- Pointer to array
- Array of pointers
- Function returning pointer
- Pointer to function returning pointer

---

## 4. Arrays & Strings

### 4.1 Arrays

- Contiguous memory
- Indexing
- Array size (`sizeof`)
- Array lifetime
- Multidimensional arrays and layout

### 4.2 Array ↔ Pointer Relationship

- Array decay to pointer
- Pointer arithmetic on arrays
- Passing arrays to functions
- Why arrays are not pointers (and where they behave like one)

### 4.3 Strings

- Null terminator convention
- String literals (read-only)
- Character arrays (writable)
- `strlen` / `strcpy` / `strcmp` / `strcat`

### 4.4 C String Problems

- Buffer overflow
- Missing null terminator
- String lifetime (stack vs heap)
- Modifying a string literal (UB)
- Unsafe copying with `strcpy`

---

## 5. Functions & Calling Mechanism

### 5.1 Functions

- Declaration vs definition
- Prototype
- Parameters and return value
- `void` functions

### 5.2 Function Call Mechanics

- Call stack
- Stack frame creation
- Arguments placed on stack / in registers
- Return address pushed
- Return value convention

### 5.3 Parameter Passing

- Pass-by-value (always in C)
- Passing pointers to simulate pass-by-reference
- What actually happens to large structs

### 5.4 Recursion

- Recursive call mechanics
- Stack growth per frame
- Base case requirement
- Stack overflow from infinite recursion

### 5.5 Calling Conventions

- Which arguments go in which registers
- Stack vs register arguments
- Return register
- Caller-saved vs callee-saved registers
- ABI (Application Binary Interface)

---

## 6. Structs, Unions & Enums

### 6.1 Structures

- Fields and their order
- Memory layout (sequential)
- Padding (alignment holes)
- Alignment rules
- Nested structs

### 6.2 Struct Pointers

- `->` operator
- Pointer-to-struct usage
- Dynamic structs on the heap

### 6.3 Structure Passing

- Pass by value (full copy)
- Pass by pointer (address only)

### 6.4 Unions

- Shared storage for all members
- Type punning
- Binary representation access

### 6.5 Enums

- Enumeration constants
- Integer representation
- State modeling

### 6.6 Bitfields

- Bit-level storage
- Packing for hardware-oriented structures
- Portability limitations

---

## 7. Type System — ⭐⭐⭐⭐

### 7.1 Type Conversion

- Implicit conversion (integer promotion, usual arithmetic conversions)
- Explicit conversion (cast)
- What information is lost

### 7.2 Qualifiers

- `const`
- `volatile`
- `restrict`

### 7.3 Type Aliases

- `typedef`

### 7.4 Composite Types

- Arrays, pointers, functions, structs, unions

### 7.5 Type Compatibility

### 7.6 Strict Aliasing

### 7.7 Effective Type

---

## 8. Compilation — ⭐⭐⭐⭐⭐

Do not treat `gcc file.c` as magic. Understand every stage.

### 8.1 Source → Executable

```
C Source
  ↓
Preprocessor   → .i file
  ↓
Compiler       → .s file (assembly)
  ↓
Assembler      → .o file (object)
  ↓
Linker         → executable (ELF)
```

### 8.2 Preprocessor

- `#include` (textual inclusion)
- `#define` macros
- Conditional compilation (`#ifdef`, `#ifndef`)
- Header guards / `#pragma once`

### 8.3 Compiler Stages

- Lexing (tokens)
- Parsing (AST)
- Semantic analysis
- Optimization
- Code generation

### 8.4 Assembly

- Registers
- Instructions
- Labels
- Stack operations
- Calling conventions in assembly

### 8.5 Object Files

- Sections (`.text`, `.data`, `.bss`, `.rodata`)
- Symbols (defined, undefined)
- Relocations

### 8.6 Linker

- Symbol resolution
- Relocation
- Static linking (`.a` archives)
- Dynamic linking (`.so` shared objects)

### 8.7 Executable Format (ELF)

- ELF header
- Sections vs segments
- Program headers
- Entry point
- `readelf` and `objdump` for inspection

### 8.8 ABI & API ⭐

- API: source-level interface
- ABI: binary-level interface (register usage, data layout, calling convention, symbol names)
- Why ABI stability matters
- How C ABI enables interoperability with Rust, Python, and other languages

> ABI is the bridge between languages. It is what makes `extern "C"` in Rust possible.

---

## 9. Assembly & Machine-Level Understanding

You do not need to become an assembly programmer. You need to understand the machine model deeply enough to read a disassembly and reason about what the CPU is doing.

### 9.1 CPU

- Registers (general-purpose, stack pointer, instruction pointer, flags)
- ALU
- Control unit
- Instruction fetch-decode-execute cycle

### 9.2 Core Instructions

- `mov` / `lea`
- `add` / `sub` / `imul` / `idiv`
- `cmp` / `test`
- `jmp` / `je` / `jne` / `jl` / `jg`
- `call` / `ret`
- `push` / `pop`

### 9.3 Machine Code

- Opcodes
- Operands
- Instruction encoding basics

### 9.4 Assembly ↔ C Mapping

- Variable → register or memory location
- Function → `call` + stack frame
- Loop → compare + conditional jump
- Pointer dereference → load from address

### 9.5 Computer Architecture ⭐⭐⭐⭐⭐

Understanding why code is fast or slow requires knowing the hardware underneath C.

#### Memory Hierarchy

```
Registers      ~1 cycle
  ↓
L1 Cache       ~4 cycles    (64 KB typical)
  ↓
L2 Cache       ~12 cycles   (512 KB typical)
  ↓
L3 Cache       ~40 cycles   (shared, 8–32 MB)
  ↓
RAM            ~100–200 cycles
  ↓
SSD/NVMe       ~100,000 cycles
```

#### Key Concepts

- Cache line (64 bytes typically)
- Spatial locality and temporal locality
- Cache miss
- False sharing (threads on same cache line)
- Branch prediction
- Instruction pipeline
- Out-of-order execution
- SIMD (single instruction, multiple data)
- Memory latency vs memory bandwidth

> You will encounter cache effects constantly when writing systems software in C or Rust. This is not optional knowledge.

---

## 10. Undefined Behavior — ⭐⭐⭐⭐⭐

This deserves its own chapter. UB is the single most dangerous concept in C.

### 10.1 What Is Undefined Behavior?

### 10.2 Why C Has UB (and Why That Is a Design Choice)

### 10.3 The Most Important UB Examples

- Out-of-bounds access
- Use-after-free
- Signed integer overflow
- Invalid pointer dereference
- Uninitialized reads
- Strict aliasing violation
- Data race
- Invalid shift

### 10.4 Compiler Assumptions Based on UB

### 10.5 Optimization and UB Interaction

### 10.6 Why "It Works on My Machine" Is Not Proof

### 10.7 Detecting UB

- UBSan
- Compiler warnings at `-Wall -Wextra -Wpedantic`
- Static analysis tools (`clang-tidy`, `cppcheck`)

---

## 11. Storage Duration & Lifetime

- Automatic storage (stack)
- Static storage (globals, `static` locals)
- Thread-local storage
- Allocated storage (heap)
- Object lifetime vs scope
- Scope ≠ lifetime
- Ownership as a mental model (who is responsible for releasing?)

> This chapter is the direct conceptual bridge to Rust. If you understand C lifetime well, Rust lifetimes will feel like enforced documentation rather than a new concept.

---

# 🦀 RUST ENTRY GATE

Complete chapters 0–11 before proceeding. See gate criteria at the top of this file.

---

# PARALLEL WITH RUST — Chapters 12–20

Study these alongside Rust. Each C topic has a direct Rust parallel.

---

## 12. Linkage & Visibility

- Local scope
- Global scope
- Internal linkage (`static`)
- External linkage (`extern`)
- Symbol visibility
- Name mangling (C vs C++)

---

## 13. C Modules & Build System

- Header files and source files
- Translation units
- Include guards / `#pragma once`
- Separate compilation
- Static libraries (`.a`)
- Shared libraries (`.so`)
- `make` / `CMake`

> Understand this alongside Rust's crate and module system — the concepts map directly.

---

## 14. File I/O & OS Interface

- Files and file descriptors
- `open` / `read` / `write` / `close`
- Standard streams (`stdin`, `stdout`, `stderr`)
- Buffering (fully buffered, line buffered, unbuffered)
- System calls
- C library vs kernel boundary

> The distinction between libc and the kernel is critical. The C standard library wraps system calls — it is not the kernel.

---

## 15. Processes — ⭐⭐⭐⭐⭐

### 15.1 Program vs Process

### 15.2 Process Address Space

- Code / text
- Data (initialized / uninitialized)
- Heap
- Stack
- Memory-mapped regions

### 15.3 Process Creation

- `fork` (copy the process)
- `exec` (replace the image)
- `fork` + `exec` pattern

### 15.4 Process Termination

- Exit status
- `wait` / `waitpid`
- Zombie processes
- Orphan processes

### 15.5 Process IDs

### 15.6 Environment Variables

### 15.7 Pipes

- Anonymous pipes (`pipe`)
- I/O redirection

### 15.8 Signals

- Signal delivery
- Signal handlers
- Common signals (`SIGINT`, `SIGTERM`, `SIGSEGV`, `SIGCHLD`)

---

## 16. Threads & Concurrency — ⭐⭐⭐⭐⭐

- Process vs thread (shared address space)
- Thread stack vs process stack
- Shared memory and race conditions
- Data races (C UB) vs race conditions (logic bug)
- Mutex (`pthread_mutex_t`)
- Semaphore
- Condition variables
- Atomic operations (`_Atomic`, `stdatomic.h`)
- Memory ordering
- Deadlocks
- Starvation
- Lock-free programming basics

> Study this directly before or alongside Rust concurrency (`Arc`, `Mutex`, `Send`, `Sync`, channels, async).

---

## 17. Virtual Memory — ⭐⭐⭐⭐⭐

- Physical memory vs virtual memory
- Virtual addresses vs physical addresses
- Pages and page size
- Page tables
- MMU (Memory Management Unit)
- TLB (Translation Lookaside Buffer)
- Page fault
- Memory-mapped files (`mmap`)
- Copy-on-write
- ASLR (Address Space Layout Randomization)

> Virtual memory completely changes how you think about pointers. Every address you see in a C program is virtual.

---

## 18. System Calls

- User mode vs kernel mode
- Privilege levels (rings)
- System call interface (`syscall` instruction)
- System call boundary
- Arguments and return values
- `errno`
- C library wrappers vs raw system calls
- `strace` for observation

---

## 19. Networking — ⭐⭐⭐⭐⭐

Networking + Rust is one of the most powerful combinations for systems engineering.

### 19.1 Network Fundamentals

- IP address
- MAC address
- Port
- Packet / frame
- Encapsulation

### 19.2 Ethernet & IP

- Ethernet frame
- IP packet structure
- ARP
- ICMP (ping)

### 19.3 Transport Layer

- TCP: connection-oriented, reliable, ordered
- UDP: connectionless, unreliable, fast
- TCP handshake (SYN / SYN-ACK / ACK)
- TCP teardown
- Flow control / congestion control

### 19.4 Application Layer

- DNS resolution
- HTTP/1.1 request/response
- TLS (conceptual overview)

### 19.5 Sockets

- Socket file descriptor
- `socket` / `bind` / `listen` / `accept` / `connect`
- `send` / `recv`
- Address structures (`sockaddr_in`, `sockaddr_in6`)

### 19.6 I/O Models

- Blocking I/O
- Non-blocking I/O
- `select` / `poll`
- `epoll` (Linux)
- Event-driven architecture

### 19.7 Server Architecture Patterns

- Single-threaded (blocking)
- Multi-process (one process per connection)
- Multi-threaded (one thread per connection)
- Event-driven (single thread, `epoll`)
- Thread pool + event loop

### 19.8 Network Concurrency

- The C10K problem
- Why threads-per-connection does not scale
- `epoll` + non-blocking sockets
- How async Rust (Tokio) maps to this model

---

## 20. Data Structures in C

Use these not just for algorithms, but to understand memory layout, pointer manipulation, and ownership patterns.

- Dynamic array (manual grow/shrink)
- Linked list (singly / doubly)
- Stack and queue
- Hash table (chaining / open addressing)
- Binary search tree
- Heap (priority queue)

> For every structure: where exactly is every byte stored? Who owns it? Who frees it?

---

# ADVANCED — Chapters 21–27

Study these after Rust fundamentals are established. They deepen your systems understanding but are not prerequisites for starting Rust.

---

## 21. Memory Allocator ⭐⭐⭐⭐⭐

Build your own `malloc`. This is elite-level foundation work.

- Why allocators exist
- Allocation strategies (first fit, best fit, segregated)
- Free lists
- Block metadata and headers
- Splitting and coalescing
- Fragmentation (internal / external)
- Alignment requirements
- `sbrk` / `mmap` for acquiring memory from the OS
- `malloc` internals (jemalloc, tcmalloc, mimalloc)
- Implement your own allocator

---

## 22. Debugging & Observability

- GDB: breakpoints, watchpoints, stack frames, register inspection, memory inspection, core dumps
- Valgrind: memcheck, callgrind, cachegrind
- Sanitizers: ASan, UBSan, TSan
- `strace` (system call tracing)
- `ltrace` (library call tracing)
- `objdump` / `readelf` / `nm`
- `perf` (performance profiling)

---

## 23. Security Fundamentals

Integrate security knowledge naturally when learning each topic:

| When learning | Introduce |
|---|---|
| Arrays / strings | Buffer overflow, unsafe copying |
| Stack | Stack smashing, stack canaries |
| Pointers / heap | Use-after-free, heap exploitation |
| Integers | Integer overflow, signedness bugs |
| Format strings | Format string vulnerability |
| System calls | Command injection, privilege escalation |

Then consolidate:

- ASLR (Address Space Layout Randomization)
- DEP / NX (Data Execution Prevention / No-Execute)
- Stack canaries
- Control-flow integrity

---

## 24. C Standard Library Internals

You need to understand the distinction between library behavior and OS/kernel behavior — not to reverse-engineer libc.

- `stdio.h`: buffered I/O over file descriptors
- `stdlib.h`: `malloc`, `free`, `exit`, `getenv`
- `string.h`: memory and string utilities
- `stdint.h` / `stddef.h` / `stdbool.h`: portable types
- `errno.h`: error reporting
- `time.h`: POSIX time

---

## 25. ABI & FFI — ⭐⭐⭐⭐⭐

This is a major concept for real-world systems work.

### 25.1 ABI Deep Dive

- Calling convention (register assignments, stack layout, alignment)
- Data layout (struct padding, endianness, pointer size)
- Symbol naming (C vs C++ name mangling)
- Dynamic linking and the PLT/GOT
- ABI stability and versioning

### 25.2 FFI (Foreign Function Interface)

- How C exposes functions to other languages
- `extern "C"` in C++ and Rust
- Linking against C libraries from Rust
- Linking against C++ from Rust (via `extern "C"` wrapper)
- `bindgen` (auto-generate Rust bindings from C headers)

### 25.3 Real-World Interop

```
Rust binary
  │
  ├── calls → libsqlite3 (C)
  ├── calls → OpenSSL (C)
  ├── calls → OS API (C ABI)
  └── wraps → C++ library (via extern "C" shim)
```

This is what production Rust systems look like.

---

## 26. Hardware Interaction

- Memory-mapped I/O
- Registers (hardware, not CPU)
- Interrupts
- DMA (Direct Memory Access)
- Device drivers
- `volatile` memory
- Embedded C
- Microcontrollers (bare-metal programming)

---

## 27. Advanced C Concepts

These are not required before Rust, but complete your deep C mastery.

- Function-like macros
- Variadic functions and `va_list`
- `setjmp` / `longjmp`
- Flexible array members
- Compound literals
- Designated initializers
- `_Generic` (type-generic macros)
- `_Atomic` (C11 atomics)
- `_Alignof` / `_Alignas`
- `__attribute__` extensions (GCC/Clang)

---

## Final Takeaway

The practical objective of this entire phase is not C mastery for its own sake. It is:

- understanding how memory is laid out and why
- knowing exactly what a pointer holds and how it can go wrong
- understanding how the compiler transforms your intentions into machine instructions
- knowing why undefined behavior is not just "unknown" but actively exploited by compilers
- seeing how the OS and hardware interact with a running process

When these ideas are clear, Rust ownership, borrowing, lifetimes, and concurrency model will feel like **the logical solution to problems you already understand**, rather than arbitrary restrictions imposed by the language.
