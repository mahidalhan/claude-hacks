---
description: Generate daily standup summary from recent codebase activity
---

# Daily Standup

Analyzes recent codebase activity to generate a structured standup summary: what was done, what's next, and any blockers.

## Process

### Step 1: Analyze Recent Activity

1. **Check git history for recent changes**:
   ```bash
   # What changed in the last 24 hours
   git log --since="24 hours ago" --oneline --all

   # Detailed changes
   git log --since="24 hours ago" --stat --all

   # Current branch status
   git status
   ```

2. **Check for any work-in-progress**:
   ```bash
   # Uncommitted changes
   git diff --stat

   # Stashed work
   git stash list
   ```

3. **Look for recent handoff documents**:
   - Check `${HANDOFF_DIR:-docs/handoffs}/` for recent entries
   - Read any handoffs from yesterday to understand context

4. **Check for pending issues** (if using GitHub):
   ```bash
   # Open issues assigned to you or recently updated
   gh issue list --state open --limit 10

   # Open PRs
   gh pr list --state open

   # PRs needing review
   gh pr list --state open --search "review-requested:@me"
   ```

### Step 2: Identify What Was Done

From the git history and handoffs, summarize:
- Features implemented
- Bugs fixed
- Refactoring completed
- Documentation updated
- Tests added

Group by logical work items, not individual commits.

### Step 3: Determine Today's Goals

Based on:
- Action items from recent handoffs
- Open PRs needing attention
- Open issues assigned
- Logical next steps from yesterday's work

Prioritize by:
1. Blocking issues / urgent bugs
2. In-progress work that needs completion
3. New feature work
4. Technical debt / cleanup

### Step 4: Identify Blockers

Check for:
- Failed CI/CD pipelines
- PRs waiting for review
- Dependencies on others
- Technical blockers discovered

## Output Format

Present the standup summary:

```markdown
# Daily Standup - [Date]

## What I Did Yesterday
- [Work item 1]: [Brief description of what was accomplished]
- [Work item 2]: [Brief description]
- [Work item 3]: [Brief description]

## What I'm Doing Today
1. **[Priority 1]**: [Description and why it's priority]
2. **[Priority 2]**: [Description]
3. **[Priority 3]**: [Description]

## Blockers / Needs Attention
- [ ] [Blocker or item needing attention]
- [ ] [PR waiting for review: #XX]

## Quick Stats
- Commits yesterday: [N]
- Files changed: [N]
- Open PRs: [N]
- Open issues: [N]
```

## Guidelines

1. **Be Concise**: Standup summaries should be scannable
2. **Focus on Outcomes**: What was achieved, not just activity
3. **Actionable Goals**: Today's items should be specific and achievable
4. **Surface Blockers Early**: Don't bury issues at the bottom
5. **Link to Context**: Reference PR numbers, issue numbers, handoff files

## Optional: Ask for Input

After presenting the summary, ask:
```
Does this capture yesterday's work accurately?
Would you like to adjust today's priorities?
```

This allows the user to correct any missed items or reprioritize.
