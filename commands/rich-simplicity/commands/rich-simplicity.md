---
description: Apply Rich Hickey's Simple Made Easy principles to code review
---

# Rich Simplicity

Follow Rich Hickey's "Simple Made Easy" principles - privileging objective simplicity over subjective ease, avoiding complecting, and favoring composable, declarative, value-oriented designs.

## Core Principle

**Choose SIMPLE over EASY.** Strive for un-braided, composable designs that minimize incidental complexity.

## Principles

### Detect Complecting
- Whenever you join concerns (state & time, data & behavior, configuration & code...) pause and seek an alternative that keeps them independent.
- Favor composition (placing things side-by-side) over interleaving.

### Prefer Values, Resist State
- Immutable data is the default.
- Mutable state must be narrowly scoped, well-named, and justified.

### Assess Constructs by Their Artifacts
- Judge a tool, abstraction, or pattern by the long-term properties of the running system it produces: clarity, changeability, and robustness.
- "Easy to start" is not sufficient.

### Declarative > Imperative
- Describe WHAT, not HOW.
- Lean on data, configuration, queries, and rule systems where possible.

### Polymorphism a la Carte
- Separate data definitions, behavior specifications, and their connections.
- Avoid inheritance hierarchies that entangle unrelated facets.

### Guard-rails Are Not Simplicity
- Tests, static checks, and refactors are valuable, but cannot compensate for a complex design. Seek to remove complexity first.

### Vigilance & Sensibility
- Continuously ask: "Is this simple? Could these parts remain independent?"
- Be willing to trade immediate ease for lasting simplicity.

## Success Criteria

A reader unfamiliar with the code should be able to locate, understand, and replace a part without untangling others.

Measure decisions by how much braid they remove, not how quickly they compile.
