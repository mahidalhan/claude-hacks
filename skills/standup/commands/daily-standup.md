---
description: Get up to speed on project status from git history, PRs, and issues
---

# Daily Standup

Generate a comprehensive project status briefing to get you up to speed after time away.

Uses the @standup skill to analyze git history, uncommitted work, PRs, issues, and handoffs.

## Usage

- `/daily-standup` - Analyze last 7 days of activity (default)
- `/daily-standup` when returning after a break - Extended analysis with context recovery

## What It Checks

- Git commits across all branches
- Uncommitted changes and stashes
- Open PRs and issues (via GitHub CLI)
- Recent handoff documents
- CI/CD status
