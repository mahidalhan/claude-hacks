# Skilled Intelligence Marketplace

**Intelligent development tools for evidence-based software engineering.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Available Plugins

Each plugin is **self-contained and independently installable**. Install only what you need.

| Plugin | Description | Skills | Commands |
|--------|-------------|--------|----------|
| **[spec-workflow](plugins/spec-workflow/README.md)** | Spec-driven development with proposal creation, TDD, and archiving | 4 skills | - |
| **[code-intelligence](plugins/code-intelligence/README.md)** | Code search and architecture analysis via Exa API | 2 skills | - |
| **[skill-tools](plugins/skill-tools/README.md)** | Deterministic skill creation with quality constraints | 1 skill | - |
| **[learning-tools](plugins/learning-tools/README.md)** | Interactive teaching with chunked explanations | 2 skills | - |
| **[creative-tools](plugins/creative-tools/README.md)** | Diagrams, UI design, generative art | 4 skills | - |
| **[workflow-tools](plugins/workflow-tools/README.md)** | Session handoffs, planning, code quality | 2 skills | 7 commands |
| **[git-tools](plugins/git-tools/README.md)** | Git commits and PR descriptions | - | 2 commands |

## Status Line Script

A custom status line script that displays real-time session information in your Claude Code terminal.

![Status Line Preview](assets/statusline-preview.png)

**Displays:**
- Current directory name
- Model name (e.g., Opus 4.5)
- Context window usage with visual progress bar
- Git branch, modified file count, and +/- line changes
- Session cost

### Setup

1. **Install jq** (required for JSON parsing):
   ```bash
   brew install jq
   ```

2. **Copy the script** to your Claude config:
   ```bash
   cp statusline.sh ~/.claude/statusline.sh
   chmod +x ~/.claude/statusline.sh
   ```

3. **Configure Claude Code**:
   ```bash
   claude config set status_line.command ~/.claude/statusline.sh
   ```

4. **Restart Claude Code** to see the status line in action.

---

## Quick Install

```bash
# Add marketplace
/plugin marketplace add mahidalhan/skilled-intelligence-marketplace

# Install individual plugins (choose what you need)
/plugin install spec-workflow@skilled-intelligence
/plugin install code-intelligence@skilled-intelligence
/plugin install skill-tools@skilled-intelligence
/plugin install learning-tools@skilled-intelligence
/plugin install creative-tools@skilled-intelligence
/plugin install workflow-tools@skilled-intelligence
/plugin install git-tools@skilled-intelligence
```

**Note**: Each plugin is fully independent and can be installed separately. Choose only the plugins you need.

Or use `/plugin` and select "Browse Plugins" for interactive installation.

## Project-Level Installation (Recommended)

Install plugins to your **project's `.claude/` directory** instead of user-level `~/.claude/` for team consistency.

Create `.claude/settings.json` in your project root:

```json
{
  "extraKnownMarketplaces": {
    "skilled-intelligence": {
      "source": {
        "source": "github",
        "repo": "mahidalhan/skilled-intelligence-marketplace"
      }
    }
  },
  "enabledPlugins": {
    "spec-workflow@skilled-intelligence": true,
    "code-intelligence@skilled-intelligence": true,
    "skill-tools@skilled-intelligence": true,
    "learning-tools@skilled-intelligence": true,
    "creative-tools@skilled-intelligence": true,
    "workflow-tools@skilled-intelligence": true,
    "git-tools@skilled-intelligence": true
  }
}
```

Start Claude Code and trust the folder — plugins install automatically.

**Benefits**: Team consistency, project isolation, version-controlled config, easy onboarding.

## Quick Start

### spec-workflow

```
Create a proposal for adding user authentication
```

Generates `proposal.md`, `tasks.md`, and `spec-delta.md` with EARS requirements.

```
Implement the add-user-auth proposal
```

### code-intelligence

```
How do I use React hooks for state management?
```

Searches billions of GitHub repos for real, working examples.

**Setup required**: Add `EXA_API_KEY=your-key` to `.env` ([Get key](https://dashboard.exa.ai/api-keys))

### skill-tools

```
Create a skill for processing CSV files
```

Guides you through deterministic skill design with quality constraints.

### learning-tools

```
Explain how React hooks work
```

Interactive explanations with chunked delivery and comprehension checks.

### creative-tools

```
Create a mermaid diagram of the authentication flow
```

Publication-quality diagrams, distinctive UI designs, and generative art.

### workflow-tools

```
/create-handoff
/resume-handoff docs/handoffs/latest.md
/daily-standup
/deslop
```

Session handoffs, code planning, and quality enforcement commands.

### git-tools

```
/commit
/describe-pr
```

Smart commits and comprehensive PR descriptions.

## Plugin Management

```bash
# List
/plugin list
/plugin marketplace list

# Update
/plugin update spec-workflow@skilled-intelligence

# Enable/Disable
/plugin enable plugin-name@skilled-intelligence
/plugin disable plugin-name@skilled-intelligence

# Uninstall
/plugin uninstall plugin-name@skilled-intelligence
/plugin marketplace remove skilled-intelligence
```

## Alternative Installation Methods

```bash
# Git URL
/plugin marketplace add https://github.com/mahidalhan/skilled-intelligence-marketplace.git

# Local development
/plugin marketplace add /path/to/skilled-intelligence-marketplace
```

## Troubleshooting

**Plugins not loading?**
1. Restart Claude Code after installation
2. Check status: `/plugin`
3. Verify marketplace: `/plugin marketplace list`

**API key errors (code-intelligence)?**
- Verify `EXA_API_KEY` in `.env`
- Install deps: `pip install requests python-dotenv`

**Plugin-specific issues?** See individual plugin READMEs.

## spec-workflow vs OpenSpec

| Feature | OpenSpec | spec-workflow |
|---------|----------|---------------|
| Installation | `npm install -g` | `/plugin install` |
| Activation | `/openspec:proposal` | Natural language |
| Platform | Standalone CLI | Claude Code |
| Dependencies | Node.js | None |

Methodology by [OpenSpec](https://github.com/Fission-AI/OpenSpec), adapted for Claude Plugins.

## Contributing

1. Fork the repo
2. Create feature branch
3. Test with real projects
4. Submit PR

## Links

- [Claude Plugins Guide](https://code.claude.com/docs/en/plugins)
- [Plugin Marketplaces](https://code.claude.com/docs/en/plugin-marketplaces)
- [OpenSpec](https://github.com/Fission-AI/OpenSpec)
- [Exa API](https://docs.exa.ai/reference/context)

## License

MIT License - See [LICENSE](LICENSE)

## Acknowledgments

- [OpenSpec](https://github.com/Fission-AI/OpenSpec) - Methodology
- [Anthropic](https://www.anthropic.com) - Claude Code
- [Exa](https://exa.ai) - Code search API
