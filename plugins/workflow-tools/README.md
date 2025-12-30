# Workflow Tools Plugin

Development workflow skills and commands for session handoffs, implementation planning, task orchestration, and code quality.

## Installation

```bash
/plugin install workflow-tools@skilled-intelligence
```

## Skills

### xml-context-engineering

Structured XML context formatting for optimal AI comprehension and response quality.

**Triggers:** "structure this context", "xml format", "optimize context"

### task-orchestrator

Task breakdown and orchestration skill for complex multi-step implementations.

**Triggers:** "orchestrate this task", "break down implementation", "plan the steps"

## Commands

### `/create-handoff`

Create a handoff document for transferring work to another session. Documents context, learnings, and next steps.

**Configuration:** Set `handoff_dir` in project's CLAUDE.md or use default `docs/handoffs/`

### `/resume-handoff [path]`

Resume work from a handoff document with context analysis and validation.

### `/plan-code-changes`

Create detailed implementation plans following Rich Hickey's "Simple Made Easy" principles.

### `/rich-simplicity`

Apply Rich Hickey's Simple Made Easy principles to code review.

### `/deslop`

Remove AI-generated code slop from recent changes (extra comments, defensive checks, style inconsistencies).

### `/test-coverage`

Analyze test coverage for recent code changes, identifying gaps and recommending test additions.

### `/daily-standup`

Generate daily standup summary from recent codebase activity: what was done, what's next, blockers.

## Configuration

Add to your project's CLAUDE.md:

```markdown
## Workflow Configuration

handoff_dir: docs/handoffs/
```
