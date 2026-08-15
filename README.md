# Systems Programming Study Plan

A structured learning path for building a deep foundation in C, computer systems, and Rust — focused on understanding how programs actually behave at the hardware, memory, and OS level.

---

## Files in This Directory

| File | Purpose |
|---|---|
| `README.md` | This file — entry point and orientation |
| `learning_timeline.md` | Phase overview and milestone checkpoints |
| `phase-1-c-fundamentals.md` | The master study map — chapters, topics, projects |
| `system-prompt.md` | AI lesson protocol — paste this to start any learning session |
| `lesson-quickref.md` | Quick-reference card for the lesson flow |

---

## Study Architecture

This is not a linear "finish C, then start Rust" plan. It is layered:

```
Chapters 0–11 (C Foundation)
        │
        ▼
🦀 Rust Entry Gate  ← understanding-based, not calendar-based
        │
        ▼
Chapters 12–20 (C + Rust in parallel)
        │
        ▼
Chapters 21–27 (Advanced Systems)
```

**Do not move forward based on time. Move forward based on Gate 2 mastery.**

---

## Study Goal

Build a mental model deep enough to reason independently about:

- how memory is laid out and why
- what pointers actually hold and how they can go wrong
- how the compiler transforms C into machine instructions
- why undefined behavior is not just a bug but a language design choice
- how the OS and hardware interact with a running process
- why Rust ownership, borrowing, and lifetimes are the natural solution to these problems

---

## Core Learning Outcomes

1. Understand how a program becomes machine instructions and runs on hardware
2. Master C memory layout, pointers, ownership models, and undefined behavior
3. Debug memory issues using GDB, Valgrind, and sanitizers
4. Understand processes, threads, system calls, virtual memory, and networking
5. Enter Rust with ownership, borrowing, and lifetimes already conceptually clear
6. Progress into serious systems work: async, networking, databases, OS internals

---

## How to Start a Session

Paste the contents of `system-prompt.md` at the start of your AI session, then say:

> "Teach Chapter X → Topic Y using our Deep Foundation Protocol."

The AI will perform a Gate 1 content audit, deliver the lesson, give leveled exercises, and perform a Gate 2 mastery validation before allowing you to advance.

---

## Reality Rule

This applies to every topic in this plan. When you observe any behavior:

| Layer | Meaning |
|---|---|
| **C language guarantee** | The standard requires this everywhere |
| **Compiler behavior** | GCC / Clang does this; others may not |
| **OS behavior** | Linux does this; macOS / Windows may differ |
| **Hardware behavior** | x86-64 does this; ARM / RISC-V may not |

Never confuse an observed behavior with a C guarantee.

---

> This roadmap is designed to build actual systems intuition, not surface familiarity.
