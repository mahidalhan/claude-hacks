# Git Tools Plugin

Git workflow commands for commits, PR descriptions, and code quality enforcement.

## Installation

```bash
/plugin install git-tools@skilled-intelligence
```

## Commands

### `/commit`

Create git commits for session changes with intelligent grouping and clear commit messages.

**Features:**
- Reviews conversation history to understand what was accomplished
- Groups related changes together
- Uses imperative mood in commit messages
- Focuses on why changes were made, not just what
- Never adds Claude attribution or co-author lines

### `/describe-pr [pr_number]`

Generate comprehensive pull request descriptions by analyzing changes and running verification.

**Features:**
- Analyzes changes and commits
- Runs automated verification (tests, lint, build)
- Creates structured PR description
- Updates existing PR or creates new one
- Links to implementation plans if available

**Usage:**
```bash
# Describe current branch's PR
/describe-pr

# Describe specific PR
/describe-pr 123
```

## Philosophy

These commands follow Rich Hickey's "Simple Made Easy" principles:
- Clear, focused changes
- Atomic commits
- Descriptive documentation
- No unnecessary complexity
