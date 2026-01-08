---
name: skill-creator
description: |
  USE WHEN: user asks to create a skill, scaffold a new capability, codify expertise into reusable instructions, or says "create skill", "new skill", "make a skill".
  DO NOT USE WHEN: user wants to use existing skills, needs general help, or is asking about skill concepts rather than creating one.
license: Complete terms in LICENSE.txt
---

This skill guides creation of exceptional Claude skills that avoid vague "be helpful" platitudes. Write deterministic instructions that produce consistent, high-quality outputs regardless of how many times they're invoked.

The user provides skill requirements: a domain to codify, an expertise to capture, a workflow to standardize, or a quality bar to enforce. They may include context about the target audience, existing patterns, or specific anti-patterns to avoid.

## Skill Thinking

Before writing any instructions, understand the expertise and commit to a DETERMINISTIC structure:
- **Domain**: What specific capability does this skill enable? What's the transformation from input to output?
- **Anti-patterns**: What does BAD output look like? Name it. ("AI slop", "tests as afterthought", "wall of boxes")
- **Quality Bar**: What separates excellent from mediocre? Be specific—vague quality is no quality.
- **Decision Points**: Where does the practitioner make choices? Codify the decision tree explicitly.

**CRITICAL**: Skills must be deterministic, not aspirational. Every instruction should constrain output. If two different Claude instances reading your skill could produce wildly different results, the skill has failed. Specificity over generality. Always.

Then write a skill file that is:
- Structured—follows the canonical 11-section format exactly
- Actionable—every sentence changes behavior, no filler
- Opinionated—takes strong positions, names anti-patterns explicitly
- Concise—40-45 lines total, ~5 bullet points per section

## Skill Excellence Guidelines

Focus on:
- **Frontmatter**: YAML header with `name` (kebab-case), `description` (when to use, what it produces), `license`. Description should contain trigger phrases ("when the user asks to...").
- **Thinking Section**: Four bullet points max. Each asks a strategic question. Format: `**Concept**: Question? Elaboration.` This forces planning before execution.
- **CRITICAL Callout**: One bold paragraph. States the non-negotiable principle. Uses strong language ("If you X, you're not doing Y"). This is the soul of the skill.
- **Guidelines Section**: Exactly 5 "Focus on" bullets. Each names a technique, then explains it. Use inline code for patterns. Be prescriptive, not descriptive.
- **NEVER Section**: Single dense paragraph listing 5-7 anti-patterns. No bullet points—flow as prose. These are the failure modes the skill prevents.
- **References**: If user explicitly requests code examples or detailed patterns, create `references/` folder with concrete examples. Keep SKILL.md lean—reference files hold the detail.
- **Command**: Always create a thin command file (`.claude/commands/{skill-name}.md`) with 2-3 lines: title, one-line description, and `Uses @{skill-name} skill.`

NEVER write vague instructions ("be thorough", "consider carefully"), omit the CRITICAL callout, exceed 45 lines, use more than 5 Focus bullets, create skills without naming specific anti-patterns, write instructions that don't constrain output ("you may choose to..."), or ship a skill without its companion command file.

Adapt skill complexity to domain scope. Narrow skills (diagram types, test patterns) need concrete examples. Broad skills (design, architecture) need decision frameworks. Meta-skills (like this one) need structural templates.

**IMPORTANT**: Match skill tone to domain culture. Technical skills use precise language. Creative skills permit more latitude. Process skills emphasize sequence. The skill should feel native to its domain, not imposed from outside.

Remember: Claude is capable of extraordinary instruction-following. Don't write weak suggestions—write strong constraints that unlock consistent excellence across every invocation.
