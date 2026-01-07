# Skilled Intelligence

**Claude Code plugin marketplace for intelligent development tools.**

## Install

```bash
# Add marketplace
/plugin marketplace add mahidalhan/skilled-intelligence-marketplace

# Install plugins
/plugin install code-intelligence@skilled-intelligence
/plugin install learning-tools@skilled-intelligence
/plugin install creative-tools@skilled-intelligence
/plugin install workflow-tools@skilled-intelligence
/plugin install skill-tools@skilled-intelligence
/plugin install git-tools@skilled-intelligence
```

## Plugins & Commands

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

## Status Line

Custom status line displaying session info. See `statusline.sh`.

```bash
brew install jq
cp statusline.sh ~/.claude/statusline.sh && chmod +x ~/.claude/statusline.sh
claude config set status_line.command ~/.claude/statusline.sh
```

## Links

- [Claude Plugins Guide](https://code.claude.com/docs/en/plugins)
- [Exa API](https://docs.exa.ai/reference/context)

## License

MIT
