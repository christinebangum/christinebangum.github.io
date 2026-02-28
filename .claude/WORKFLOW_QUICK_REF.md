# Workflow Quick Reference

**Model:** Contractor (you direct, Claude orchestrates)

---

## The Loop

```
Your instruction
    ↓
[PLAN] (if multi-file or unclear) → Show plan → Your approval
    ↓
[EXECUTE] Implement, verify, done
    ↓
[REPORT] Summary + what's ready
    ↓
Repeat
```

---

## I Ask You When

- **Design forks:** "Option A (fast) vs. Option B (robust). Which?"
- **Code ambiguity:** "Spec unclear on X. Assume Y?"
- **Results surprise:** "Coefficient flipped sign after adding controls. Investigate?"
- **Scope question:** "Also run robustness check Y while here, or focus on X?"

---

## I Just Execute When

- Code fix is obvious (bug, syntax error)
- Verification (Stata log checks, LaTeX compilation)
- Documentation (logs, commits)
- Plotting (per established standards)

---

## Quality Gates (No Exceptions)

| Score | Action |
|-------|--------|
| >= 80 | Ready to commit |
| < 80  | Fix blocking issues |

---

## Non-Negotiables

- **Relative paths** in all Stata .do files (use globals set in master.do)
- **`set seed`** once at top of master.do for any stochastic code
- **Publication-quality figures** — white background, high DPI, journal-appropriate fonts/sizes
- **Confidential data** never committed — data/ directory is always gitignored
- **Overleaf is authoritative** — local .tex is for review only

---

## Preferences

<!-- Fill in as you discover your working style -->

**Visual:** Publication-ready; journal-style formatting; no draft-quality output
**Reporting:** Structured and precise; concise but thorough
**Session logs:** Always (post-plan, incremental, end-of-session)
**Rigor:** Thoroughness over speed; double-check results

---

## Exploration Mode

For experimental work, use the **Fast-Track** workflow:
- Work in `explorations/` folder
- 60/100 quality threshold (vs. 80/100 for production)
- No plan needed — just a research value check
- See `.claude/rules/exploration-fast-track.md`

---

## Next Step

You provide task → I plan (if needed) → Your approval → Execute → Done.
