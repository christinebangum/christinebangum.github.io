# Constitutional Governance: Job Market Paper

**Define immutable principles vs. flexible preferences for this project.**

---

## Article I: Single Source of Truth

Overleaf `.tex` is authoritative for paper text. Stata `.do` files are authoritative for empirical analysis. Output files (tables, figures) are derived artifacts — never hand-edit.

**Exceptions:** Christine may instruct Claude to edit the local .tex directly for specific fixes.

---

## Article II: Plan-First Threshold

Enter plan mode for tasks requiring >3 files, >30 minutes, or multi-step workflows.

**Exceptions:** Exploration folder allows fast-track. Quick fixes (typos, single-line changes) skip planning.

---

## Article III: Quality Gate

Nothing commits below 80/100. Publication-ready visuals at all times.

**Exceptions:** Exploratory work in `explorations/` uses 60/100 threshold. Draft commits explicitly tagged as such.

---

## Article IV: Verification Standard

All Stata scripts must run without errors. All LaTeX must compile successfully. Output tables must match Stata log values.

**Exceptions:** Known issues documented in session log.

---

## Article V: Data Confidentiality

Confidential administrative data never committed to version control. No individual-level data displayed. Cell counts above minimum reporting thresholds.

**Exceptions:** None. This is non-negotiable.

---

## User Preferences (Override Anytime)

- Figure color scheme (to be determined as we work)
- Table formatting details (estout options)
- Citation style preferences
- Comment verbosity in .do files
- Reporting detail level (concise vs detailed)

---

## Requesting Amendment

When deviating from an article, ask:

> "Are you **amending Article X** (permanent change) or **overriding for this task** (one-time exception)?"
