# Plan: Portable Skills Migration

> **Status**: Ready for execution
> **Created**: 2024-12-30
> **Source repos**: tannery_app, epiphany-OS-desktop-app, residency

## Objective

Consolidate duplicated skills/commands from project repos into the skilled-spec marketplace, making them portable and maintainable from a single source of truth.

---

## Phase 1: Create New Plugin Scaffolds

Create 4 new plugin directories with proper structure and manifests.

### 1.1 learning-tools plugin

```bash
mkdir -p plugins/learning-tools/.claude-plugin
mkdir -p plugins/learning-tools/skills/explainer
mkdir -p plugins/learning-tools/skills/threaded-explainer/references
```

**Create `plugins/learning-tools/.claude-plugin/plugin.json`:**
```json
{
  "name": "learning-tools",
  "version": "1.0.0",
  "description": "Interactive teaching skills with chunked explanations, comprehension checks, and interrupt handling. Use for explaining code, concepts, or learning on-the-go.",
  "author": {
    "name": "Mahid Alhan",
    "url": "https://github.com/mahidalhan"
  },
  "repository": "https://github.com/mahidalhan/skilled-intelligence-marketplace",
  "license": "MIT",
  "keywords": ["learning", "teaching", "explainer", "education", "comprehension"]
}
```

**Create `plugins/learning-tools/README.md`** with skill descriptions.

### 1.2 creative-tools plugin

```bash
mkdir -p plugins/creative-tools/.claude-plugin
mkdir -p plugins/creative-tools/skills/mermaid-diagrams
mkdir -p plugins/creative-tools/skills/frontend-design
mkdir -p plugins/creative-tools/skills/algorithmic-art/templates
mkdir -p plugins/creative-tools/skills/ascii-art-explainer
```

**Create `plugins/creative-tools/.claude-plugin/plugin.json`:**
```json
{
  "name": "creative-tools",
  "version": "1.0.0",
  "description": "Creative output skills for diagrams, UI design, generative art, and visual explanations. Produces publication-quality Mermaid diagrams, distinctive frontends, and ASCII visualizations.",
  "author": {
    "name": "Mahid Alhan",
    "url": "https://github.com/mahidalhan"
  },
  "repository": "https://github.com/mahidalhan/skilled-intelligence-marketplace",
  "license": "MIT",
  "keywords": ["mermaid", "diagrams", "frontend", "design", "ascii", "art", "visualization"]
}
```

### 1.3 workflow-tools plugin

```bash
mkdir -p plugins/workflow-tools/.claude-plugin
mkdir -p plugins/workflow-tools/skills/xml-context-engineering
mkdir -p plugins/workflow-tools/skills/task-orchestrator
mkdir -p plugins/workflow-tools/commands
```

**Create `plugins/workflow-tools/.claude-plugin/plugin.json`:**
```json
{
  "name": "workflow-tools",
  "version": "1.0.0",
  "description": "Development workflow skills for session handoffs, implementation planning, task orchestration, and XML context structuring. Enables seamless multi-session work.",
  "author": {
    "name": "Mahid Alhan",
    "url": "https://github.com/mahidalhan"
  },
  "repository": "https://github.com/mahidalhan/skilled-intelligence-marketplace",
  "license": "MIT",
  "keywords": ["workflow", "handoff", "planning", "orchestration", "xml", "context"]
}
```

### 1.4 git-tools plugin

```bash
mkdir -p plugins/git-tools/.claude-plugin
mkdir -p plugins/git-tools/commands
```

**Create `plugins/git-tools/.claude-plugin/plugin.json`:**
```json
{
  "name": "git-tools",
  "version": "1.0.0",
  "description": "Git workflow commands for commits, PR descriptions, and code quality enforcement. Follows Rich Hickey's Simple Made Easy principles.",
  "author": {
    "name": "Mahid Alhan",
    "url": "https://github.com/mahidalhan"
  },
  "repository": "https://github.com/mahidalhan/skilled-intelligence-marketplace",
  "license": "MIT",
  "keywords": ["git", "commit", "pull-request", "workflow", "quality"]
}
```

---

## Phase 2: Migrate Skills

Copy skills from source repos, using the best/most complete version.

### 2.1 learning-tools skills

| Skill | Source | Destination |
|-------|--------|-------------|
| explainer | `/Users/mahidalhan/code/epiphany-OS-desktop-app/.claude/skills/explainer/SKILL.md` | `plugins/learning-tools/skills/explainer/SKILL.md` |
| threaded-explainer | `/Users/mahidalhan/code/epiphany-OS-desktop-app/.claude/skills/threaded-explainer/` | `plugins/learning-tools/skills/threaded-explainer/` |

**Note**: Copy entire threaded-explainer folder including `references/output-examples.md`

### 2.2 creative-tools skills

| Skill | Source | Destination |
|-------|--------|-------------|
| mermaid-diagrams | `/Users/mahidalhan/code/epiphany-OS-desktop-app/.claude/skills/mermaid-diagrams/SKILL.md` | `plugins/creative-tools/skills/mermaid-diagrams/SKILL.md` |
| frontend-design | `/Users/mahidalhan/code/epiphany-OS-desktop-app/.claude/skills/frontend-design/SKILL.md` | `plugins/creative-tools/skills/frontend-design/SKILL.md` |
| algorithmic-art | `/Users/mahidalhan/code/tannery_app/.claude/skills/creative/algorithmic-art/` | `plugins/creative-tools/skills/algorithmic-art/` |
| ascii-art-explainer | `/Users/mahidalhan/code/tannery_app/.claude/skills/creative/ascii-art-explainer/SKILL.md` | `plugins/creative-tools/skills/ascii-art-explainer/SKILL.md` |

**Note**: Copy entire algorithmic-art folder including `templates/`

### 2.3 workflow-tools skills

| Skill | Source | Destination |
|-------|--------|-------------|
| xml-context-engineering | `/Users/mahidalhan/code/epiphany-OS-desktop-app/.claude/skills/xml-context-engineering/SKILL.md` | `plugins/workflow-tools/skills/xml-context-engineering/SKILL.md` |
| task-orchestrator | `/Users/mahidalhan/code/tannery_app/.claude/skills/workflow/task-orchestrator/SKILL.md` | `plugins/workflow-tools/skills/task-orchestrator/SKILL.md` |

### 2.4 Upgrade skill-tools

Replace existing skill-creator with claude-skill-creator-ultra:

| Source | Destination |
|--------|-------------|
| `/Users/mahidalhan/code/epiphany-OS-desktop-app/.claude/skills/claude-skill-creator-ultra/SKILL.md` | `plugins/skill-tools/skills/skill-creator/SKILL.md` |

**Action**: Overwrite the existing file with the ultra version content.

---

## Phase 3: Migrate Commands

Template commands for portability using `$ARGUMENTS` where needed.

### 3.1 workflow-tools commands

| Command | Source | Modifications |
|---------|--------|---------------|
| create-handoff | `/Users/mahidalhan/code/tannery_app/.claude/commands/workflow/create-handoff.md` | Replace `openspec/handoffs/` with `$HANDOFF_DIR` or project-configurable path |
| resume-handoff | `/Users/mahidalhan/code/epiphany-OS-desktop-app/.claude/commands/resume-handoff.md` | Same path templating |
| plan-code-changes | `/Users/mahidalhan/code/epiphany-OS-desktop-app/.claude/commands/plan-code-changes.md` | Keep as-is (project-agnostic) |
| rich-simplicity | `/Users/mahidalhan/code/epiphany-OS-desktop-app/.claude/commands/rich-simplicity.md` | Keep as-is (philosophy doc) |

**Templating pattern for handoff commands:**

```markdown
<!-- At top of command file -->
> **Configuration**: Set `handoff_dir` in project's CLAUDE.md or use default `docs/handoffs/`

- Create your file under `${HANDOFF_DIR:-docs/handoffs}/YYYY-MM-DD_HH-MM-SS_description.md`
```

### 3.2 git-tools commands

| Command | Source | Modifications |
|---------|--------|---------------|
| commit | `/Users/mahidalhan/code/tannery_app/.claude/commands/git/commit.md` | Keep as-is |
| describe-pr | `/Users/mahidalhan/code/tannery_app/.claude/commands/git/describe_pr.md` | Keep as-is |

### 3.3 quality commands (add to workflow-tools or separate)

| Command | Source | Decision |
|---------|--------|----------|
| deslop | `/Users/mahidalhan/code/tannery_app/.claude/commands/quality/deslop.md` | Add to workflow-tools/commands/ |
| test-coverage | `/Users/mahidalhan/code/tannery_app/.claude/commands/quality/test-coverage.md` | Add to workflow-tools/commands/ |

---

## Phase 4: Update Marketplace Documentation

### 4.1 Update root README.md

Add new plugins to the table:

```markdown
| Plugin | Description | Skills | Commands |
|--------|-------------|--------|----------|
| **[spec-workflow](plugins/spec-workflow/README.md)** | Spec-driven development | 4 skills | - |
| **[code-intelligence](plugins/code-intelligence/README.md)** | Code search via Exa API | 2 skills | - |
| **[skill-tools](plugins/skill-tools/README.md)** | Skill creation (ultra) | 1 skill | - |
| **[learning-tools](plugins/learning-tools/README.md)** | Interactive teaching | 2 skills | - |
| **[creative-tools](plugins/creative-tools/README.md)** | Diagrams, design, art | 4 skills | - |
| **[workflow-tools](plugins/workflow-tools/README.md)** | Handoffs, planning | 2 skills | 6 commands |
| **[git-tools](plugins/git-tools/README.md)** | Git workflow | - | 2 commands |
```

### 4.2 Create individual README.md for each new plugin

Each plugin needs a README with:
- Description
- Skills list with trigger phrases
- Commands list with usage examples
- Setup instructions (if any)

---

## Phase 5: Cleanup Source Repos (Optional)

After migration is complete and tested, consider:

1. **Remove duplicates** from tannery_app and epiphany
2. **Add plugin dependency** in their `.claude/settings.json`:

```json
{
  "enabledPlugins": {
    "learning-tools@skilled-intelligence": true,
    "creative-tools@skilled-intelligence": true,
    "workflow-tools@skilled-intelligence": true,
    "git-tools@skilled-intelligence": true
  }
}
```

3. **Keep project-specific skills** that don't make sense as portable:
   - `swift-debug` (epiphany - Swift-specific)
   - `agent-config-sync` (tannery_app - project-specific)
   - `session-context` (tannery_app - may be project-specific)

---

## Execution Checklist

```
[ ] Phase 1: Create plugin scaffolds
    [ ] 1.1 learning-tools structure + plugin.json
    [ ] 1.2 creative-tools structure + plugin.json
    [ ] 1.3 workflow-tools structure + plugin.json
    [ ] 1.4 git-tools structure + plugin.json

[ ] Phase 2: Migrate skills
    [ ] 2.1 Copy explainer, threaded-explainer
    [ ] 2.2 Copy mermaid-diagrams, frontend-design, algorithmic-art, ascii-art-explainer
    [ ] 2.3 Copy xml-context-engineering, task-orchestrator
    [ ] 2.4 Upgrade skill-creator to ultra version

[ ] Phase 3: Migrate commands
    [ ] 3.1 Template and copy handoff commands
    [ ] 3.2 Copy git commands
    [ ] 3.3 Copy quality commands

[ ] Phase 4: Documentation
    [ ] 4.1 Update root README.md
    [ ] 4.2 Create README for each new plugin

[ ] Phase 5: Test
    [ ] Install plugins locally
    [ ] Verify skills trigger correctly
    [ ] Test commands work

[ ] Phase 6: Cleanup (optional)
    [ ] Remove duplicates from source repos
    [ ] Add plugin dependencies to source repos
```

---

## File Inventory

**Total new files to create:**
- 4 plugin.json files
- 4 README.md files (per plugin)
- 8 SKILL.md files (migrated)
- 1 references/output-examples.md (threaded-explainer)
- 1 templates/ directory (algorithmic-art)
- 8 command .md files (migrated)

**Files to modify:**
- 1 README.md (root marketplace)
- 1 SKILL.md (skill-creator upgrade)

---

## Commands to Start Next Session

```
Resume this plan: /resume-handoff PLAN-portable-skills-migration.md

Or simply:
"Execute the portable skills migration plan in PLAN-portable-skills-migration.md"
```
