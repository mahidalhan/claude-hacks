---
description: Create handoff document for transferring work to another session
---

> **Configuration**: Set `handoff_dir` in project's CLAUDE.md or use default `docs/handoffs/`

# Create Handoff

You are tasked with writing a handoff document to hand off your work to another agent in a new session. You will create a handoff document that is thorough, but also **concise**. The goal is to compact and summarize your context without losing any of the key details of what you're working on.


## Process

### 1. Filepath & Metadata

Use the following information to understand how to create your document:
- Create your file under `${HANDOFF_DIR:-docs/handoffs}/YYYY-MM-DD_HH-MM-SS_description.md`, where:
    - YYYY-MM-DD is today's date
    - HH-MM-SS is the hours, minutes and seconds based on the current time, in 24-hour format (use `13:00` for `1:00 pm`)
    - description is a brief kebab-case description
- Get the current git commit hash and branch name for metadata
- Examples:
    - `docs/handoffs/2025-01-08_13-55-22_create-context-compaction.md`

### 2. Handoff Writing

Using the above conventions, write your document. Use the defined filepath and the following YAML frontmatter pattern:

```markdown
---
date: [Current date and time with timezone in ISO format]
researcher: Claude
git_commit: [Current commit hash]
branch: [Current branch name]
topic: "[Feature/Task Name] Implementation Strategy"
tags: [implementation, strategy, relevant-component-names]
status: complete
last_updated: [Current date in YYYY-MM-DD format]
type: implementation_strategy
---

# Handoff: {very concise description}

## Task(s)
{Description of the task(s) that you were working on, along with the status of each (completed, work in progress, planned/discussed). If you are working on an implementation plan, make sure to call out which phase you are on. Make sure to reference the plan document and/or research document(s) you are working from that were provided to you at the beginning of the session, if applicable.}

## Critical References
{List any critical specification documents, architectural decisions, or design docs that must be followed. Include only 2-3 most important file paths. Leave blank if none.}

## Recent Changes
{Describe recent changes made to the codebase that you made in file:line syntax}

## Learnings
{Describe important things that you learned - e.g. patterns, root causes of bugs, or other important pieces of information someone that is picking up your work after you should know. Consider listing explicit file paths.}

## Artifacts
{An exhaustive list of artifacts you produced or updated as filepaths and/or file:line references - e.g. paths to feature documents, implementation plans, etc that should be read in order to resume your work.}

## Action Items & Next Steps
{A list of action items and next steps for the next agent to accomplish based on your tasks and their statuses}

## Other Notes
{Other notes, references, or useful information - e.g. where relevant sections of the codebase are, where relevant documents are, or other important things you learned that you want to pass on but that don't fall into the above categories}
```

### 3. Verify and Report

After creating the handoff document, verify it was written correctly by reading it back.

Once this is completed, respond to the user with:

```
Handoff created! You can resume from this handoff in a new session with the following command:

/resume-handoff ${HANDOFF_DIR:-docs/handoffs}/YYYY-MM-DD_HH-MM-SS_description.md
```

---

## Additional Notes & Instructions

- **More information, not less**. This is a guideline that defines the minimum of what a handoff should be. Always feel free to include more information if necessary.
- **Be thorough and precise**. Include both top-level objectives, and lower-level details as necessary.
- **Avoid excessive code snippets**. While a brief snippet to describe some key change is important, avoid large code blocks or diffs; do not include one unless it's necessary (e.g. pertains to an error you're debugging). Prefer using `/path/to/file.ext:line` references that an agent can follow later when it's ready.
- **Reference existing docs**. If there are existing plan documents that are relevant, reference them.
