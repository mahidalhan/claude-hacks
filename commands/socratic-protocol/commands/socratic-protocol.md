---
description: Socratic method for resolving ambiguity in planning, conflicts, or any unclear situation
---

# Socratic Protocol

Use this protocol whenever facing ambiguity: planning, conflict resolution, design decisions, or unclear requirements.

---

## When to Invoke

- Planning a feature with multiple valid approaches
- Resolving conflicts between plans/tasks (e.g., `/ralph-parallel`)
- Design decisions with tradeoffs
- Unclear or underspecified requirements
- Architecting systems or workflows
- Any situation where guessing would be wrong

---

## Phase 1: Load Context

Before asking anything:
1. Explore relevant code/files
2. Understand existing patterns and constraints
3. **Read `docs/learnings/index.md`** if it exists (past learnings)
4. Build informed mental model

**First message must demonstrate context:**
> "I've read X, Y, Z. Here's what I understand: [summary]. But I need clarity on..."

Never ask what you could answer from code.

---

## Phase 2: Edge Case & Failure Analysis

**MANDATORY for planning/architecting.** Depth scales with intensity.

### 2.0 Determine Intensity (ALWAYS DO THIS FIRST)

**Before any analysis, explicitly state the intensity level:**

> "Task intensity: [LEVEL] because [reason]"

| Intensity | When to Use | Edge Cases | Failures | Time |
|-----------|-------------|------------|----------|------|
| **LOW** | Bug fix, typo, single-line change, config tweak | 3-5 | 2-3 | 2 min |
| **MEDIUM** | New feature, refactor, multi-file change | 10-20 | 5-10 | 5-10 min |
| **HIGH** | Architecture, new system, workflow design, integration | 30-50+ | 15-25 | 20-30 min |
| **CRITICAL** | Production system, data pipeline, security, money | Exhaustive | Exhaustive | 1+ hour |

**Intensity Signals:**
```
LOW       → "fix", "tweak", "update", "rename", single file
MEDIUM    → "add feature", "refactor", "implement", 2-5 files
HIGH      → "architect", "design system", "workflow", "integrate", 5+ files
CRITICAL  → "production", "payments", "auth", "data migration", "security"
```

**Skip Phase 2 entirely for LOW intensity** - just note 2-3 obvious edge cases inline.
**Full Phase 2 required for MEDIUM+** - enumerate systematically.

### 2.1 Edge Cases (Things That CAN Happen)

Edge cases are **boundary conditions, unexpected inputs, rare but valid scenarios**.
They are inputs/scenarios your design must HANDLE.

**Enumerate by category (scale depth by intensity):**

#### Input/Data
```
Null/Empty     : null, undefined, "", [], {}, 0, false
Boundaries     : min-1, min, max, max+1, overflow
Size           : 0, 1, few, many, huge (10MB+)
Type           : wrong type, mixed types, coerced types
Format         : malformed, truncated, corrupted, partial
Encoding       : unicode, emoji, RTL, control chars, injection
Precision      : float rounding, date/time, timezone
Special values : NaN, Infinity, reserved words, path traversal
```

#### State
```
Lifecycle      : uninitialized, initializing, ready, stale, disposed
Concurrency    : simultaneous access, partial update, race window
Persistence    : missing file, corrupted, locked, permissions denied
Cache          : cold, warm, stale, invalidated, oversized
Sync           : ahead, behind, diverged, conflicted
```

#### Environment
```
Resources      : disk full, memory pressure, CPU throttled
Network        : offline, slow, timeout, partial response
Dependencies   : unavailable, rate-limited, deprecated API, version mismatch
Permissions    : denied, elevated, sandboxed
Platform       : OS version, locale, timezone
```

#### User/Interaction
```
Sequence       : out of order, repeated, cancelled mid-way
Timing         : too fast, too slow, exactly at threshold
Interruption   : app backgrounded, killed, crashed, restored
Undo/Redo      : after state change, with side effects
```

**Output format:**
```markdown
### Edge Cases (n enumerated)

| # | Category | Edge Case | Handling |
|---|----------|-----------|----------|
| 1 | Input | File path is empty string | Validate, return error |
| 2 | State | Index.md doesn't exist | Create default, continue |
| ... | ... | ... | ... |
```

### 2.2 Failures (Things That WILL Break)

Failures are **breakages, degradations, bugs that will occur in production**.
They are problems your design must PREVENT or DETECT.

**Enumerate by category:**

#### Degradation (Gradual)
```
Memory         : leaks accumulate, fragments, eventual OOM
Performance    : slows over time, thrashing, starvation
Data           : drift, staleness, inconsistency growth
Quality        : signal-to-noise degrades, noise accumulates
```

#### Catastrophic (Sudden)
```
Crash          : uncaught exception, assertion, segfault, panic
Corruption     : partial write, race condition, double-free
Deadlock       : circular wait, resource starvation
Data loss      : overwrite, truncation, failed rollback
```

#### Silent (Undetected)
```
Logic          : wrong result returned, bad input accepted
Integration    : components diverge, contract violated silently
Security       : vulnerability exposed, privilege escalation
Observability  : failure happens but not logged/alerted
```

**Output format:**
```markdown
### Failures (n enumerated)

| # | Type | Failure | Prevention | Detection |
|---|------|---------|------------|-----------|
| 1 | Degradation | Context grows unbounded | Compaction | Monitor size |
| 2 | Silent | Stale learning applied | Timestamp + SHA | User reports regression |
| ... | ... | ... | ... | ... |
```

### 2.3 Cross-Product Analysis (CRITICAL intensity only)

For critical systems, enumerate cross-products:
- What if [edge case A] + [edge case B] simultaneously?
- What if [failure X] occurs during [edge case Y]?

### 2.4 Triage

```
MUST SOLVE    : High impact + Certain/Likely → Design must address
SHOULD SOLVE  : Medium impact OR Possible → Design should address
ACCEPT        : Low impact, rare → Document and accept
```

Surface any MUST SOLVE without mitigation to user via `AskUserQuestion`.

---

## Phase 3: Socratic Interview

Use `AskUserQuestion` tool with informed options.

**Rules:**
- Always include a **recommended option** (mark with "(Recommended)", list first)
- Base recommendation on Phase 1 context + Phase 2 analysis
- Ask 2-3 questions per round max
- Follow threads, challenge vague answers
- Continue until confident

**Question Types:**

| Situation | Question Style |
|-----------|----------------|
| Planning | "Which approach for X? A does Y, B does Z" |
| Conflict | "File X touched by both. Who owns it?" |
| Design | "Tradeoff: simplicity vs flexibility. Priority?" |
| Requirements | "You said X. Does that mean Y or Z?" |
| Edge Cases | "How should we handle [edge case]?" |
| Failures | "Risk X has no mitigation. Accept or redesign?" |

---

## Phase 4: Confirm & Proceed

Before acting, explicitly confirm:
> "Based on your answers: [summary]. Ready to proceed?"

**Include analysis summary:**
> "Edge cases handled: n. Failures mitigated: m. Risks accepted: [list]."

**If planning:** Write spec to `docs/plan/` with:
- Open questions at top (if any remain)
- **Edge Cases & Failures section** (from Phase 2)
- Concise implementation phases
- Specific code changes per phase

**If resolving:** Apply the decision and document rationale.

---

## Phase 5: Capture Learnings (Post-Execution)

After execution completes, if corrections were needed:

1. **Capture correction** via `/capture-learning`
2. **Link to plan** that generated the error
3. **Categorize**: Pattern | Anti-Pattern | File Rule

This feeds back into Phase 1 for future invocations.

---

## Integration with Other Skills

Other skills invoke this protocol for ambiguity:

```markdown
# In another skill:
If ambiguous → invoke `/socratic-planner` to resolve, then continue.
If architecting → MUST run Phase 2 (Edge Case & Failure Analysis).
```

Skills that use Socratic:
- `/ralph-parallel` - conflict resolution + edge case analysis
- `/plan-code-changes` - feature planning + failure analysis
- `/capture-learning` - surfaces for compaction decisions
- Any skill facing unclear requirements
