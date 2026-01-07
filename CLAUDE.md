# Skilled Intelligence Marketplace

Flat marketplace of individual skills and commands. Install only what you need.

## Structure

```
skilled-intelligence/
├── .claude-plugin/
│   └── marketplace.json        # Single source of truth for all plugins
├── skills/
│   └── {skill-name}/           # Each skill is its own installable plugin
│       ├── skills/
│       │   └── {skill-name}/
│       │       └── SKILL.md    # Skill definition
│       └── commands/           # Related commands (optional)
│           └── {command}.md
├── commands/
│   └── {command-name}/         # Standalone commands (no skill)
│       └── commands/
│           └── {command}.md
├── README.md
└── CLAUDE.md
```

## Available Plugins

### Skills (with optional commands)
| Plugin | Command | Description |
|--------|---------|-------------|
| standup | /daily-standup | Project status briefing from git/PRs/issues |
| exa-code-context | /code-search | Search GitHub for real code examples |
| architecture-introspector | /analyze-architecture | First-principles architecture analysis |
| explainer | /explain | Interactive chunked explanations |
| threaded-explainer | /threaded-explainer | Deep-dive nested topic threads |
| mermaid-diagrams | /diagram | Publication-quality Mermaid diagrams |
| frontend-design | /design-ui | Distinctive UI design |
| algorithmic-art | /generative-art | Procedural generative art |
| ascii-art-explainer | /ascii-explain | ASCII art visualizations |
| xml-context-engineering | /xml-context | XML context structuring for LLMs |
| task-orchestrator | /orchestrate | Multi-step task planning |
| skill-creator | /create-skill | Scaffold new skills |

### Commands (standalone)
| Plugin | Commands | Description |
|--------|----------|-------------|
| git-commit | /commit | Create git commits for session changes |
| describe-pr | /describe-pr | Generate PR descriptions |
| handoff | /create-handoff, /resume-handoff | Session continuity |
| plan-code-changes | /plan-code-changes | Implementation planning |
| deslop | /deslop | Remove over-engineering |
| rich-simplicity | /rich-simplicity | Simple Made Easy review |
| test-coverage | /test-coverage | Test coverage analysis |

<critical_learnings>
## Maintenance Rules

### Flat Structure (CRITICAL)
Each skill/command is its own installable plugin. Users install individual capabilities, not bundles.

**Adding a new skill:**
1. Create `skills/{skill-name}/skills/{skill-name}/SKILL.md`
2. Optionally add `skills/{skill-name}/commands/{command}.md`
3. Add entry to marketplace.json
4. Commit and push

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

### Command Naming
Command filename = command name. No configuration needed.
- `daily-standup.md` → `/daily-standup`
- `commit.md` → `/commit`

### No plugin.json Needed
Individual plugins do NOT need `.claude-plugin/plugin.json`. The marketplace.json handles all metadata. Auto-discovery finds commands/ and skills/ directories.

### Single README Policy
All documentation in root README.md. No per-skill READMEs. Prevents drift.

### Testing Changes
Always test in a SEPARATE project after pushing:
```bash
/plugin marketplace update skilled-intelligence
/plugin install {plugin-name}@skilled-intelligence
```
</critical_learnings>

<skill_authoring>
## Skill File Format

```markdown
---
name: skill-name
description: One-line description for auto-discovery
license: MIT
---

Core instruction content here.

## Thinking Section (optional)
Planning instructions before output.

## Output Format
Mandatory structure requirements.

## Excellence Guidelines
Quality criteria and anti-patterns.
```
</skill_authoring>

<command_authoring>
## Command File Format

```markdown
---
description: Short description shown in command picker
---

# Command Title

What this command does.

Uses the @skill-name skill for [purpose].

## Usage
- `/command-name arg1`
- `/command-name arg2`
```

Commands invoke skills via `@skill-name` reference.
</command_authoring>

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

- [Claude Plugins Guide](https://code.claude.com/docs/en/plugins)
- [Plugin Marketplaces](https://code.claude.com/docs/en/plugin-marketplaces)
