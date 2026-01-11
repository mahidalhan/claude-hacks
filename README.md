# Claude Hacks

**Skills, commands, and hacks for Claude Code.**

Extend Claude Code with custom skills, slash commands, and utilities. Install what you need, skip what you don't.

---

## Hacks (Zero Install)

Standalone scripts. Copy once, use forever.

### Status Line

![Status Line Preview](assets/statusline-preview.png)

Custom status line: directory | model | context % | git status | cost

```bash
brew install jq
curl -o ~/.claude/statusline.sh https://raw.githubusercontent.com/mahidalhan/claude-hacks/master/hacks/statusline.sh
chmod +x ~/.claude/statusline.sh
claude config set status_line.command ~/.claude/statusline.sh
```

### Publish Skill

Publish skills from any project to your own marketplace repo. Copies skill, bumps version, commits & pushes.

```bash
# Install
curl -o ~/.local/bin/publish-skill https://raw.githubusercontent.com/mahidalhan/claude-hacks/master/hacks/publish-skill
chmod +x ~/.local/bin/publish-skill

# Set your marketplace (add to .zshrc)
export CLAUDE_MARKETPLACE=~/code/my-marketplace

# Usage (from any project with .claude/skills/)
publish-skill my-skill                            # From .claude/skills/my-skill
publish-skill my-skill --source /path/to/skill    # Custom source
publish-skill my-skill --dry-run                  # Preview changes
```

---

## Plugins (Marketplace)

```bash
# Add marketplace (once)
/plugin marketplace add mahidalhan/claude-hacks

# Install any plugin
/plugin install <plugin-name>@claude-hacks
```

### code-intelligence
Code search and architecture analysis via Exa API (requires `EXA_API_KEY`).

| Command | Description |
|---------|-------------|
| `/code-search` | Search GitHub repos for real code examples |
| `/analyze-architecture` | First-principles architecture analysis |

Skills: `exa-code-context`, `architecture-introspector`

### learning-tools
Interactive teaching with chunked explanations and comprehension checks.

| Command | Description |
|---------|-------------|
| `/explain` | Recursive ground-up explanations |
| `/threaded-explainer` | Chunked explanations with interrupt handling |

Skills: `explainer`, `threaded-explainer`

### creative-tools
Diagrams, UI design, generative art, and visual explanations.

| Command | Description |
|---------|-------------|
| `/diagram` | Mermaid diagrams for any flow |
| `/design-ui` | Distinctive frontend designs |
| `/generative-art` | Algorithmic/generative art |
| `/ascii-explain` | ASCII art visualizations |

Skills: `mermaid-diagrams`, `frontend-design`, `algorithmic-art`, `ascii-art-explainer`

### workflow-tools
Session handoffs, planning, orchestration, and development workflows.

| Command | Description |
|---------|-------------|
| `/create-handoff` | Create session handoff document |
| `/resume-handoff` | Resume from handoff |
| `/orchestrate` | Multi-task orchestration |
| `/plan-code-changes` | Implementation planning |
| `/daily-standup` | Generate standup summary |
| `/deslop` | Remove AI slop from text |
| `/rich-simplicity` | Apply Simple Made Easy principles |
| `/test-coverage` | Analyze test coverage |
| `/xml-context` | Structure context with XML |

Skills: `task-orchestrator`, `xml-context-engineering`

### skill-tools
Create custom Claude skills with quality constraints.

| Command | Description |
|---------|-------------|
| `/create-skill` | Scaffold a new skill |

Skills: `skill-creator`

### git-tools
Smart commits and PR descriptions following best practices.

| Command | Description |
|---------|-------------|
| `/commit` | Generate semantic commit |
| `/describe-pr` | Generate PR description |

---

## Links

- [Claude Plugins Guide](https://code.claude.com/docs/en/plugins)
- [Exa API](https://docs.exa.ai/reference/context)

## License

MIT
