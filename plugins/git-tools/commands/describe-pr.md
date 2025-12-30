---
description: Generate comprehensive pull request descriptions
arguments:
  - name: pr_number
    description: PR number to describe (optional - uses current branch if not provided)
    required: false
---

# Generate PR Description

You are tasked with generating comprehensive pull request descriptions by analyzing changes, running tests, and creating structured documentation.

## Initial Response

When this command is invoked:

1. **Check if PR number provided via `$ARGUMENTS`**:
   - If $ARGUMENTS contains a PR number, use it directly
   - Otherwise, check for existing PR in current branch

2. **Check for existing PR**:
   ```bash
   gh pr view --json url,number,title,state
   ```

3. **If no PR found**: Work with current branch changes
4. **If PR exists**: Work with the existing PR to update description

## PR Description Generation Process

### Step 1: Gather PR Information

1. **Read PR template** (if exists):
   ```bash
   ls .github/pull_request_template.md .github/PULL_REQUEST_TEMPLATE.md
   ```

2. **Analyze changes**:
   ```bash
   # Get PR diff and commits
   gh pr diff [number] || git diff main...HEAD
   gh pr view [number] --json commits || git log main...HEAD --oneline

   # Check current status
   git status --porcelain
   ```

3. **Identify implementation plan** (if available):
   - Search for related plan documents
   - Read plan to understand original scope and requirements

### Step 2: Run Verification Tests

Execute automated verification and document results:

```bash
# Run test suite (adapt to project)
npm test || pytest || make test

# Check code quality
npm run lint || make check

# Verify build
npm run build || make build
```

### Step 3: Generate PR Description

Create structured PR description:

```markdown
## What problem was I solving?
[Clear problem statement - what user pain point or requirement this addresses]

## What user-facing changes did I ship?
[Specific changes users will see - new features, UI changes, behavior modifications]

## How I implemented it
[Technical approach - key architectural decisions, patterns used, integration points]

### Key Changes:
- **Backend**: [API changes, database changes, business logic]
- **Frontend**: [UI components, pages, user interactions]
- **Tests**: [New test coverage, test patterns]

## How to verify it

### Automated Verification:
- [ ] Tests pass
- [ ] Build succeeds
- [ ] Linting passes

### Manual Testing:
- [ ] [Step 1]
- [ ] [Step 2]

## Description for changelog
[One-line summary for release notes]

## Additional Notes
[Any implementation details, known limitations, or follow-up work needed]
```

### Step 4: Update PR with Description

```bash
# Update the PR description
gh pr edit [number] --body-file /path/to/description.md

# Or create PR if none exists
gh pr create --title "[Title]" --body-file /path/to/description.md
```

## PR Analysis Patterns

### For Feature Implementation:
- Focus on user benefit and technical approach
- Include before/after comparisons if UI changes
- Document any breaking changes or migration steps

### For Bug Fixes:
- Explain the bug and its impact
- Describe root cause analysis
- Show how the fix addresses the issue

### For Refactoring:
- Justify why the refactoring was needed
- Highlight maintainability improvements
- Confirm no behavior changes

## Important Guidelines

1. **Focus on user impact** - Start with what users will experience
2. **Be specific about verification** - Include exact steps to test
3. **Run actual verification** - Execute commands and mark checkboxes accurately
4. **Document deviations** - Note if implementation differs from original scope
5. **Think about reviewers** - Provide context they need to understand changes
