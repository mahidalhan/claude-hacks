---
description: Analyze test coverage for recent code changes
---

# Test Coverage Check

Analyzes test coverage for user changes in the codebase, identifying untested code paths and recommending test additions.

## When to Use

- After implementing a feature or making code changes
- Before committing to ensure adequate test coverage
- During code review to validate test completeness

## Analysis Process

### Step 1: Identify Changed Files

1. **Get git diff**:
   ```bash
   # Get unstaged changes
   git diff

   # Get staged changes
   git diff --cached

   # Get changes from last N commits
   git diff HEAD~N..HEAD
   ```

2. **Categorize changes**:
   - Backend code (APIs, services, utilities)
   - Frontend code (components, pages, hooks)
   - Schema/migrations
   - Test files

### Step 2: Map Code to Tests

For each changed file:

1. **Backend Changes**:
   - **API endpoints**: Check for E2E tests and integration tests
   - **Services**: Check for unit tests covering business logic
   - **Utilities**: Check for unit tests

2. **Frontend Changes**:
   - **Pages**: Check for E2E tests covering user journeys
   - **Components**: Check for component tests if complex logic exists
   - **Hooks**: Check for tests covering hook usage scenarios

### Step 3: Identify Coverage Gaps

For each changed file, determine:

1. **Missing Test Files**:
   - File changed but no corresponding test file exists
   - Test file exists but doesn't cover the changed code paths

2. **Incomplete Coverage**:
   - Happy path tested but error paths missing
   - Auth checks not tested
   - Edge cases not covered
   - Validation logic not tested

### Step 4: Generate Coverage Report

Create a structured report:

```markdown
# Test Coverage Report

**Generated**: [timestamp]
**Changes Analyzed**: [commit range or diff summary]

## Summary

- **Files Changed**: [count]
- **Files with Tests**: [count]
- **Files Missing Tests**: [count]
- **Coverage Gaps**: [count]

## Detailed Analysis

### [file_path]
- **Change Type**: [API endpoint / Service / Component / etc.]
- **Test Status**: Covered / Partial / Missing
- **Existing Tests**: [test files that cover this]
- **Coverage Gaps**:
  - [ ] Missing test for [scenario]
  - [ ] Error path not covered: [scenario]
- **Recommendations**:
  - Add test: [scenario description]

## Priority Actions

### High Priority (Critical Paths)
1. [Action] - [Reason]

### Medium Priority (Important Features)
1. [Action] - [Reason]

### Low Priority (Edge Cases)
1. [Action] - [Reason]
```

## Coverage Rules

### Must Have Tests

1. **All API Endpoints**:
   - Test covering happy path
   - Test covering auth failure
   - Test covering validation errors

2. **All Services** (if extracted):
   - Unit tests for business logic
   - Tests for error handling

3. **Complex Frontend Logic**:
   - E2E tests for user journeys
   - Component tests for complex state management

## Tips

- Focus on critical paths first (auth, core business logic)
- Don't require tests for trivial changes (typos, formatting)
- Consider test cost vs. value (complex logic > simple getters)
- Use E2E tests for user-facing features, unit tests for business logic
