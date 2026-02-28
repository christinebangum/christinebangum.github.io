---
name: context-status
description: Show current context status and session health. Use to check active plan, session log, and preservation state.
allowed-tools: ["Read", "Bash", "Glob"]
---

# /context-status — Check Session Health

Show the current session status including active plan, session log, and preservation state.

## Workflow

### Step 1: Find Active Plan

```bash
ls -lt quality_reports/plans/*.md 2>/dev/null | head -3
```

### Step 2: Find Session Log

```bash
ls -lt quality_reports/session_logs/*.md 2>/dev/null | head -1
```

### Step 3: Check Git State

```bash
git status --short
git log --oneline -3
```

### Step 4: Check MEMORY.md Size

```bash
wc -l MEMORY.md
```

### Step 5: Report Status

```
Session Status
-------------------------------------
Active Plan
  File:   quality_reports/plans/YYYY-MM-DD_description.md
  Status: [draft | approved | in_progress | completed]

Session Log
  File:   quality_reports/session_logs/YYYY-MM-DD_description.md

Git State
  Branch: [current branch]
  Uncommitted changes: [yes/no]

Memory
  MEMORY.md: [N] lines (limit: 200)

Preservation Check
  - Plans on disk: [yes/no]
  - Session log current: [yes/no]
  - MEMORY.md up to date: [yes/no]
```
