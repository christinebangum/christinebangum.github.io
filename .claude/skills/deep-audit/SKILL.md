---
name: deep-audit
description: Repository-wide consistency audit. Checks that all configuration files, rules, skills, and agents are consistent and correct. Use after broad changes or before releases.
allowed-tools: ["Read", "Write", "Edit", "Bash", "Glob", "Grep", "Agent"]
---

# /deep-audit — Repository Consistency Audit

Run a comprehensive consistency audit across the repository.

## When to Use

- After broad changes (new skills, rules, workflow modifications)
- Before major commits
- When asked to "find inconsistencies", "audit", or "check everything"

## Workflow

### Phase 1: Audit

Check these areas:

#### 1. CLAUDE.md Accuracy
- Skills table matches actual skill directories in `.claude/skills/`
- Folder structure description matches reality
- Commands are correct and would execute

#### 2. Rules Consistency
- Valid YAML frontmatter with correct `paths:` references
- No contradictions between rules
- All templates referenced in rules exist in `templates/`

#### 3. Skills Consistency
- Valid YAML frontmatter in all SKILL.md files
- `allowed-tools` values are sensible
- No references to removed skills (Quarto, slides, R)

#### 4. Agents Consistency
- Valid YAML frontmatter in all agent files
- Agent tools match available tools
- No references to removed agents

#### 5. Cross-Document Consistency
- No stale references to Quarto, Beamer slides, R, or lectures
- Quality gate rubrics match actual file types in the project
- .gitignore covers all artifact types mentioned in rules

### Phase 2: Fix All Issues

For each finding:
1. Read the file first
2. Apply the fix
3. Verify the fix

### Phase 3: Report

```markdown
## Audit Results

| # | Severity | File | Issue | Status |
|---|----------|------|-------|--------|
| 1 | Critical | path | Description | Fixed/Open |

### Result: [CLEAN | N issues remaining]
```
