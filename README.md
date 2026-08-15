# System Design Study Plan

This repository contains a structured learning path for building a strong foundation in systems programming, low-level computing, and Rust.

## Contents

- [learning_timeline.md](learning_timeline.md) — milestone-based roadmap from C fundamentals to serious systems Rust
- [phase-1-c-fundamentals.md](phase-1-c-fundamentals.md) — detailed C foundations study map with exercises and outcomes

## Study Goal

The goal is not to memorize syntax, but to understand how programs actually behave at the hardware, memory, and OS boundaries.

## Core Learning Outcomes

1. Understand how a program becomes machine instructions and runs on hardware.
2. Master C memory layout, pointers, ownership models, and undefined behavior.
3. Debug memory issues using tools such as GDB, Valgrind, and sanitizers.
4. Understand processes, threads, system calls, and virtual memory.
5. Transition into Rust with ownership, borrowing, lifetimes, and concurrency.
6. Progress into serious systems work: networking, async, databases, and operating systems.

## Suggested Sequence

- Phase 1: C fundamentals and memory model
- Phase 2: C systems internals and debugging
- Phase 3: Rust fundamentals and ownership
- Phase 4: Rust deeper concepts and concurrency
- Phase 5: Serious systems Rust and advanced topics

## How to Use This Plan

- Learn the concept
- Write small experiments or code snippets
- Debug the program with tools
- Re-explain the concept in your own words
- Build a small project before moving on

## Milestone Rule

Do not move to the next major topic until you can explain:

- what the code is doing
- where the data lives in memory
- what the CPU/OS is responsible for
- what can go wrong and why

---

> This roadmap is designed to build actual systems intuition, not just superficial familiarity.
