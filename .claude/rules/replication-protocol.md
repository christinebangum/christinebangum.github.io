# Replication-First Protocol

**Core principle:** Verify results reproduce exactly BEFORE extending or modifying.

---

## Phase 1: Inventory & Baseline

Before modifying any Stata code:

- [ ] Read the existing master.do and understand the pipeline
- [ ] Inventory all .do files, data inputs, and outputs
- [ ] Record current results (point estimates, SEs, N) as gold standard:

```markdown
## Current Results Baseline

| Target | Table/Figure | Value | SE | N | Notes |
|--------|-------------|-------|----|---|-------|
| Main effect | Table X, Col Y | -X.XXX | (X.XXX) | N | Primary specification |
```

- [ ] Store baseline in `quality_reports/replication_baseline.md`

---

## Phase 2: Verify Reproducibility

- [ ] Run `master.do` from scratch on a clean environment
- [ ] Compare all outputs against the baseline
- [ ] Document any discrepancies

### Tolerance Thresholds

| Type | Tolerance | Rationale |
|------|-----------|-----------|
| Integers (N, counts) | Exact match | No reason for any difference |
| Point estimates | < 0.001 | Numerical precision |
| Standard errors | < 0.001 | Same estimation procedure |
| P-values | Same significance level | Display rounding |

### If Mismatch

**Do NOT proceed to modifications.** Isolate which script introduces the difference, check common causes (sample restriction, variable definition, clustering), and document the investigation.

---

## Phase 3: Only Then Modify

After baseline is verified:

- [ ] Commit verified baseline: "Verify baseline results — all targets match"
- [ ] Make modifications incrementally (one specification change at a time)
- [ ] After each change, re-verify that unaffected results remain stable
- [ ] Document what changed and why in the session log

---

## Stata-Specific Notes

### Common Reproducibility Issues

| Issue | Symptom | Fix |
|-------|---------|-----|
| Sort order instability | Slightly different results across runs | Use `sort varlist, stable` or `set seed` before random operations |
| Package version differences | Results differ across machines | Document `ssc install` requirements in master.do |
| Missing value handling | Wrong N | Check `if` conditions vs `in` ranges |
| Factor variable base category | Different coefficients | Explicitly set base with `ib#.varname` |
| Merge many-to-many | Silent duplication | Always use `m:1` or `1:m` with `assert` |
