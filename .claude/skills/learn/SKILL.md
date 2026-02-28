---
name: learn
description: Extract reusable knowledge from the current session into a persistent skill. Use when you discover something non-obvious or develop a reusable workflow.
argument-hint: "[skill-name (kebab-case)]"
allowed-tools: ["Read", "Write", "Bash", "Glob", "Grep"]
---

# /learn — Skill Extraction Workflow

Extract non-obvious discoveries into reusable skills that persist across sessions.

## When to Use This Skill

Invoke `/learn` when you encounter:

- **Non-obvious debugging** — investigation that took significant effort
- **Misleading errors** — error message was wrong, found the real cause
- **Workarounds** — found a limitation with a creative solution
- **Repeatable workflows** — multi-step task you'd do again
- **Stata tricks** — undocumented behavior or useful patterns

## Workflow

### Phase 1: Evaluate

1. "What did I just learn that wasn't obvious before starting?"
2. "Would future-me benefit from this being documented?"
3. "Is this a multi-step workflow I'd repeat?"

**Continue only if YES to at least one.**

### Phase 2: Check Existing Skills

```bash
ls .claude/skills/ 2>/dev/null
grep -r -i "KEYWORD" .claude/skills/ 2>/dev/null
```

### Phase 3: Create Skill

Create at `.claude/skills/[skill-name]/SKILL.md` with:
- Problem description
- Trigger conditions
- Step-by-step solution
- Verification steps
- Example

### Phase 4: Quality Gates

- [ ] Description has specific trigger conditions
- [ ] Solution was verified to work
- [ ] Content is specific enough to be actionable
- [ ] Content is general enough to be reusable
- [ ] No sensitive information

## Also Update MEMORY.md

Add a `[LEARN:category]` entry for the discovery.
