# Meta-Governance: Project Workflow Standards

**This repository hosts Claude Code workflow configuration for Christine's job market paper project.**

---

## Memory Management

### MEMORY.md (root directory, committed)

**Purpose:** Project learnings that persist across sessions

**What goes here:**
- Workflow improvements: `[LEARN:workflow] Spec-then-plan reduces rework`
- Tool discoveries: `[LEARN:stata] Use `margins` for marginal effects after probit`
- Paper decisions: `[LEARN:paper] Reviewer suggested adding pre-trends test`
- Data lessons: `[LEARN:data] Donation variable is zero-inflated, needs careful treatment`

**Size limit:** Keep under 200 lines

---

### .claude/state/personal-memory.md (gitignored, local only)

**Purpose:** Machine-specific learnings

**What goes here:**
- Machine setup: `[LEARN:setup] Stata-MP path is /usr/local/stata17/stata-mp`
- Local paths: `[LEARN:files] Data stored at /secure/data/donations/`
- Tool quirks: `[LEARN:latex] Need texlive-full for this machine`

---

## Dogfooding: Following Our Own Workflow

### Plan-First
- Enter plan mode for non-trivial tasks (>3 files, >1 hour, multi-step)
- Save plans to `quality_reports/plans/YYYY-MM-DD_description.md`

### Quality Gates
- Nothing ships below 80/100
- Run quality scoring before commits

### Context Survival
- Update MEMORY.md with [LEARN] entries after sessions
- Save active plans to disk before compression
- Keep session logs current
