# Claude Hacks

Skills, commands, and hacks for Claude Code. Install only what you need.

## Structure

```
claude-hacks/
├── .claude-plugin/
│   └── marketplace.json        # Single source of truth for all plugins
├── skills/
│   └── {skill-name}/           # Each skill is its own installable plugin
│       └── skills/
│           └── {skill-name}/
│               └── SKILL.md    # Skill definition (auto-invocable)
├── commands/
│   └── {command-name}/         # Standalone commands (no skill)
│       └── commands/
│           └── {command}.md
├── README.md
└── CLAUDE.md
```

## Available Plugins

### Skills (auto-invocable by Claude)
Skills are now directly invocable by Claude Code based on their description—no wrapper commands needed.

| Skill | Trigger Phrases | Description |
|-------|-----------------|-------------|
| standup | "status", "brief me", "catch up" | Project status briefing from git/PRs/issues |
| exa-code-context | "find examples", "code search" | Search GitHub for real code examples |
| architecture-introspector | "analyze architecture", "review design" | First-principles architecture analysis |
| explainer | "explain", "teach me", "how does X work" | Interactive chunked explanations |
| threaded-explainer | "deep dive", "explain in threads" | Deep-dive nested topic threads |
| mermaid-diagrams | "diagram", "visualize", "flowchart" | Publication-quality Mermaid diagrams |
| frontend-design | "design UI", "build interface" | Distinctive UI design |
| algorithmic-art | "generative art", "create art" | Procedural generative art |
| ascii-art-explainer | "ASCII diagram", "terminal visual" | ASCII art visualizations |
| xml-context-engineering | "structure context", "XML tags" | XML context structuring for LLMs |
| task-orchestrator | "orchestrate", "plan tasks" | Multi-step task planning |
| skill-creator | "create skill", "new skill" | Scaffold new skills |

### Commands (user-invoked via `/command`)
| Plugin | Commands | Description |
|--------|----------|-------------|
| git-commit | /commit | Create git commits for session changes |
| describe-pr | /describe-pr | Generate PR descriptions |
| handoff | /create-handoff, /resume-handoff | Session continuity |
| plan-code-changes | /plan-code-changes | Implementation planning |
| deslop | /deslop | Remove over-engineering |
| rich-simplicity | /rich-simplicity | Simple Made Easy review |
| test-coverage | /test-coverage | Test coverage analysis |

<ultrathink_guide>
## ULTRATHINK: Deep Thinking Mode

Claude Code supports extended thinking with trigger words that allocate more reasoning tokens:
- **"think"** → baseline thinking budget
- **"think hard"** → increased budget
- **"think harder"** → more budget
- **"ultrathink"** → maximum budget (31,999 tokens)

### When to Use ULTRATHINK

Best for:
- Architectural decisions with multi-system tradeoffs
- Complex debugging after 2+ failed attempts
- System-wide analysis spanning 10+ components
- Critical migrations and legacy system work
- Multi-step orchestration with non-obvious dependencies

NOT for:
- Simple code questions
- Bug fixes with obvious solutions
- Tasks that don't require deep reasoning
- Every request (wastes tokens/cost)

### Skills with ULTRATHINK Support

These skills benefit from deep thinking:
- **architecture-introspector** - First-principles analysis across all 6 phases
- **task-orchestrator** - Comprehensive dependency graph mapping
- **xml-context-engineering** - Thorough attention economics analysis

Example usage:
```
ultrathink and analyze the architecture of this codebase
think harder about the task dependencies here
```
</ultrathink_guide>

<critical_learnings>
## Maintenance Rules

### Flat Structure (CRITICAL)
Each skill/command is its own installable plugin. Users install individual capabilities, not bundles.

**Adding a new skill:**
1. Create `skills/{skill-name}/skills/{skill-name}/SKILL.md`
2. Add entry to marketplace.json
3. Commit and push

**Adding a standalone command:**
1. Create `commands/{command-name}/commands/{command}.md`
2. Add entry to marketplace.json
3. Commit and push

### Version Bumping (CRITICAL)
Claude Code caches plugins by version. Changes are INVISIBLE until version is bumped.

**When to bump version:**
- Any content changed in SKILL.md or command files
- Any file added or removed

**How:**
```json
// In marketplace.json, find the plugin entry
"version": "1.0.0"  // bump to "1.0.1"
```

### Skills Are Auto-Invocable (NEW)
As of Claude Code 2.1, skills are visible in the slash command menu by default and Claude can auto-invoke them based on description. No wrapper commands needed.

To opt-out of slash menu visibility:
```yaml
---
name: skill-name
user-invocable: false  # Hide from slash menu
---
```

### No plugin.json Needed
Individual plugins do NOT need `.claude-plugin/plugin.json`. The marketplace.json handles all metadata. Auto-discovery finds commands/ and skills/ directories.

### Single README Policy
All documentation in root README.md. No per-skill READMEs. Prevents drift.

### Testing Changes
Always test in a SEPARATE project after pushing:
```bash
/plugin marketplace update claude-hacks
/plugin install {plugin-name}@claude-hacks
```
</critical_learnings>

<skill_authoring>
## Skill File Format

```markdown
---
name: skill-name
description: |
  USE WHEN: trigger conditions, user phrases, task types that match.
  DO NOT USE WHEN: conditions where this skill is not appropriate.
  Optional: requirements like API keys or dependencies.
license: MIT
---

Core instruction content here.

## Thinking Section (optional)
Planning instructions before output.

## Output Format
Mandatory structure requirements.

## Excellence Guidelines
Quality criteria and anti-patterns.

## Deep Thinking Mode (for complex skills)
When to use "think harder" or "ultrathink".
```

### Description Best Practices

Descriptions control auto-invocation accuracy. Use the WHEN/WHEN NOT pattern:

**Good** (high accuracy):
```yaml
description: |
  USE WHEN: analyzing existing architectures, evaluating decisions, identifying technical debt.
  DO NOT USE WHEN: simple code questions, bug fixes, feature implementation.
```

**Bad** (low accuracy):
```yaml
description: Analyzes architecture  # Too vague, will misfire
```
</skill_authoring>

<command_authoring>
## Command File Format

Commands are for user-initiated actions that shouldn't auto-invoke.

```markdown
---
description: Short description shown in command picker
---

# Command Title

What this command does.

## Usage
- `/command-name arg1`
- `/command-name arg2`
```
</command_authoring>

## New Claude Code Features (v2.1)

Features relevant to plugin development:

- **Skill hot-reload**: Changes in skills/ directories immediately available
- **Agent field**: Specify agent type in skill frontmatter: `agent: Explore`
- **Context fork**: Run skills in forked context: `context: fork`
- **Hooks in skills**: Define `PreToolUse`, `PostToolUse`, `Stop` hooks in skill lifecycle
- **YAML allowed-tools**: Cleaner tool restrictions in frontmatter

## Development Workflow

1. Create skill/command in appropriate directory
2. Add entry to marketplace.json with version "1.0.0"
3. Test locally in this repo
4. Commit and push
5. Test in separate project with marketplace update

## Tools Available

- GitHub CLI (`gh`)
- Git

## Links

- [Claude Code Skills Docs](https://code.claude.com/docs/en/skills)
- [Claude Plugins Guide](https://code.claude.com/docs/en/plugins)
- [Plugin Marketplaces](https://code.claude.com/docs/en/plugin-marketplaces)
