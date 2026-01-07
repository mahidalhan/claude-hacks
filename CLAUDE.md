# Skilled Intelligence Marketplace

Claude Code plugin marketplace providing intelligent development tools.

## Structure

```
skilled-intelligence/
├── .claude-plugin/
│   └── marketplace.json        # Single source of truth for all plugins
├── plugins/
│   └── {plugin-name}/
│       ├── commands/           # Slash commands (auto-discovered)
│       │   └── {command}.md    # /command-name
│       └── skills/             # Skills (auto-discovered)
│           └── {skill-name}/
│               ├── SKILL.md    # Skill definition with YAML frontmatter
│               └── references/ # Supporting docs (optional)
├── README.md                   # All documentation lives here
└── CLAUDE.md                   # This file
```

## Plugins

| Plugin | Skills | Commands |
|--------|--------|----------|
| code-intelligence | exa-code-context, architecture-introspector | /code-search, /analyze-architecture |
| learning-tools | explainer, threaded-explainer | /explain, /threaded-explainer |
| creative-tools | mermaid-diagrams, frontend-design, algorithmic-art, ascii-art-explainer | /diagram, /design-ui, /generative-art, /ascii-explain |
| workflow-tools | task-orchestrator, xml-context-engineering | /create-handoff, /resume-handoff, /orchestrate, /plan-code-changes, /daily-standup, /deslop, /rich-simplicity, /test-coverage, /xml-context |
| skill-tools | skill-creator | /create-skill |
| git-tools | - | /commit, /describe-pr |

<critical_learnings>
## Maintenance Rules

### Version Bumping (CRITICAL)
Claude Code caches plugins by version. Changes to commands/skills are INVISIBLE to users until version is bumped in marketplace.json.

**When to bump version:**
- Any command added, removed, or renamed
- Any skill content changed
- Any file structure changed

**How:**
```json
// .claude-plugin/marketplace.json
"version": "1.0.2"  // bump to "1.0.3"
```

### Command Naming
Command filename = command name. No configuration needed.
- `teach.md` → `/teach`
- `threaded-explainer.md` → `/threaded-explainer`

To rename a command: `git mv old.md new.md` + bump version

### No plugin.json Needed
Individual plugins do NOT need `.claude-plugin/plugin.json`. The marketplace.json handles all metadata. Auto-discovery finds commands/ and skills/ directories.

### Single README Policy
All documentation in root README.md. No per-skill or per-plugin READMEs. Prevents drift and maintenance overhead.

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

1. Make changes to skills/commands
2. Test locally in this repo
3. Bump version in marketplace.json
4. Commit and push
5. Test in separate project with marketplace update

## Tools Available

- GitHub CLI (`gh`)
- Git

## Links

- [Claude Plugins Guide](https://code.claude.com/docs/en/plugins)
- [Plugin Marketplaces](https://code.claude.com/docs/en/plugin-marketplaces)
