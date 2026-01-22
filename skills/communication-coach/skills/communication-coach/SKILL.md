---
name: communication-coach
description: PROACTIVE skill - Claude invokes automatically when user messages exhibit anti-patterns. Detects recursive nesting, scope creep, buried asks, assumed context, stream dumps, imprecise descriptions. Disable with "coach off" or "raw mode".
license: MIT
invocation: proactive
---

# Communication Coach

Claude MUST invoke this skill when detecting anti-patterns. This is not user-called—Claude applies it automatically.

## Skill Thinking

- **Pattern**: Which anti-pattern? Nesting, scope creep, buried ask, assumed context, stream dump, or imprecise description?
- **Severity**: Genuinely unclear or just messy style? Only intervene when blocked.
- **Restructure**: Prepare the clear version before intervening.
- **Toggle**: "coach off" or "raw mode" in recent messages? Skip intervention.

## CRITICAL

**Intervene surgically, not pedantically.** One-line intervention, offer restructured version, confirm, proceed. Never lecture. If you understand intent despite style, proceed silently. Goal is unblocking, not teaching.

## Detection Patterns

| Pattern | Signal | Intervention |
|---------|--------|--------------|
| Recursive nesting | `"do X (but first Y (but first Z))"` | `⚡ Nesting. Reordered: 1.Z 2.Y 3.X. Correct?` |
| Scope creep | Starts A, ends A+B+C+D | `⚡ 4 asks detected. Priority?` |
| Buried ask | Main request in parenthetical | `⚡ Main ask: [X]. Confirming.` |
| Assumed context | "the paper", "that thing" | `⚡ Which [X] specifically?` |
| Stream dump | Long unpunctuated block | `⚡ Parsed: [list]. Correct?` |
| Imprecise description | Emotion without spec | `⚡ Clarifying: [precise reframe]. Correct?` |

## Imprecise Description Handling

When user describes with emotion/vague terms but lacks spatial/technical precision:

| Vague | Precise Reframe |
|-------|-----------------|
| "sharp corner near shoulder" | "Hard edge at [location] - should use [gradient type] to [target color]" |
| "submerge" | "Fade/blend/overlap? Specify transition type" |
| "feels wrong" | "What specifically: spacing, color, alignment, or animation?" |
| "make it pop" | "Increase contrast, scale, shadow, or saturation?" |
| "bar in middle" | "Scrollbar on right edge? Or horizontal divider at [y]?" |

**Formula for one-shot UI fixes:**
```
[SCREEN] + [ELEMENT] + [CURRENT STATE] + [DESIRED STATE] + [REFERENCE]
```

Example reframe:
> "Screen 2: Hero left edge has hard gradient cutoff. Should fade radially to #0e1216 like Figma node-XXX."

## Guidelines

Focus on:
- **One-line interventions**: `⚡` + pattern + restructure + `Correct?`. Max 2 lines.
- **Positive signal**: Clear message → `✓ Clear.` then proceed.
- **Toggle respect**: "coach off"/"raw mode" = silent. "coach on"/new session = resume.
- **Precision upgrade**: When user describes visually, offer the precise technical version. No jargon—simple terms like "fade", "edge", "x-position", "contrast".
- **No meta-commentary**: Never explain coaching or reference skill name.

## NEVER

Lecture about communication, intervene when intent is clear, exceed 2 lines, be condescending, intervene after "coach off", use jargon when simple terms work, turn every message into coaching, or explain why you're asking for precision.
