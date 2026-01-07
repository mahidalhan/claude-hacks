# Threaded Explainer Output Templates

## Standard Mode (Primary Question)

```
╭─ THREAD ───────────────────────────────────────╮
│ Q₀: [User's question]                          │
╰────────────────────────────────────────────────╯

┌─ GAP ──────────────────────────────────────────┐
│ Filling: [Core concept being explained]        │
│ Foundation: [Prerequisites being established]  │
└────────────────────────────────────────────────┘

>> 1 ── [Topic] ──────────────────────────────────
Level 1: [Foundation explanation - what IS this?]
[3-5 sentences establishing the absolute basics]

>> 2 ── [Topic] ──────────────────────────────────
Level 1: [Continue foundation OR...]
Level 2: [Build on >> 1 - HOW does it work?]
[3-5 sentences building on previous chunk]

>> 3 ── [Topic] ──────────────────────────────────
[Next concept chunk]

? Check: [Comprehension question about >> 1 - >> 3]

>> 4 - >> 6: [Remaining topics preview]
```

## Interrupt Mode (Sub-question at >> 3)

When user asks about something FROM chunk >> 3 before reading >> 4 - >> 6:

```
╭─ INTERRUPT @ >> 3 ───────────────────────────────╮
│ Q₀: [Original question]                        │
│  └→ Q₁: [Sub-question] (sparked at >> 3)        │
│ PENDING: >> 4 - >> 6                                 │
╰────────────────────────────────────────────────╯

┌─ GAP ──────────────────────────────────────────┐
│ Filling: [What Q₁ clarifies]                   │
│ Serves Q₀: [How this deepens original answer]  │
└────────────────────────────────────────────────┘

## Brief Answer (Q₁)
[3-5 lines ONLY - concise, direct answer]
[No verbose expansion - interrupt mode is lean]

Integration: [One line on how this enhances >> 3]

───────────────────────────────────────────────────
## Resuming Q₀ from >> 4
───────────────────────────────────────────────────

>> 4 ── [Topic] ──────────────────────────────────
[Continues explanation, NOW INFORMED by Q₁'s answer]
[May weave Q₁ insight naturally into the flow]

>> 5 ── [Topic] ──────────────────────────────────
[Next chunk]

? Check: [Comprehension question covering >> 3 - >> 5]

>> 6: [Final topic preview]
```

## Nested Interrupt (Q₂ during Q₁'s resume)

When curiosity sparks AGAIN during the resumed content:

```
╭─ INTERRUPT @ >> 5 ───────────────────────────────╮
│ Q₀: [Original]                                 │
│  └→ Q₁(>> 3): [First sub-question] ✓            │
│      └→ Q₂: [New sub-question] (sparked at >> 5)│
│ PENDING: >> 6                                    │
╰────────────────────────────────────────────────╯

┌─ GAP ──────────────────────────────────────────┐
│ Filling: [What Q₂ clarifies]                   │
│ Serves Q₁: [How it connects to first sub-Q]   │
│ Serves Q₀: [How it ultimately answers origin] │
└────────────────────────────────────────────────┘

## Brief Answer (Q₂)
[3-5 lines - even more concise at deeper nesting]

Integration: [How Q₂ + Q₁ together enrich >> 5]

───────────────────────────────────────────────────
## Resuming Q₀ from >> 6 (Final)
───────────────────────────────────────────────────

>> 6 ── [Topic] ──────────────────────────────────
[Final chunk, synthesizing all thread insights]

## Thread Synthesis
Now that we've explored:
- Q₀: [Original answer, enhanced by sub-threads]
- Q₁: [How first detour deepened understanding]
- Q₂: [How second detour added precision]

[2-3 sentences tying the complete thread together]
```

## Verbosity Modes

| Trigger | Mode | Chunk Count | Lines/Chunk |
|---------|------|-------------|-------------|
| Primary question | Full | 5-8 | 4-6 |
| Interrupt question | Brief | 1-2 | 3-4 |
| "Expand >> n" | Deep | 3-5 on topic | 5-7 |
| "Quick answer" | Minimal | 0 | 2-3 total |

## Lineage Notation Quick Reference

- `Q₀` = Original question
- `Q₁(>> 3)` = Follow-up sparked at chunk 3
- `Q₁ ✓` = Previously answered, now resolved
- `PENDING: >> 4 - >> 6` = Chunks not yet delivered
- `[Q₀ → Q₁(>> 3) → Q₂]` = Full thread chain (inline)

## Comprehension Check Patterns

```
? Check: What would happen if [edge case]?
? Check: In your own words, why does [mechanism]?
? Check: Given [scenario], which [choice] applies?
? Check: What's the difference between [A] and [B] we just covered?
```

Wait for response. If gap revealed, address before >> (n+1).
