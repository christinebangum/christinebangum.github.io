---
paths:
  - "code/**/*.do"
  - "**/*.tex"
  - "output/**"
---

# Quality Gates & Scoring Rubrics

## Thresholds

- **80/100 = Commit** -- good enough to save
- **90/100 = PR** -- ready for review
- **95/100 = Finalize** -- publication-ready

## Stata Scripts (.do)

| Severity | Issue | Deduction |
|----------|-------|-----------|
| Critical | Syntax errors (won't run) | -100 |
| Critical | Hardcoded absolute paths | -20 |
| Critical | Missing `set seed` for stochastic code | -15 |
| Critical | Wrong sample restriction | -30 |
| Critical | Wrong clustering level for standard errors | -20 |
| Major | Data files not gitignored | -10 |
| Major | No comments explaining key decisions | -5 |
| Major | Missing variable labels | -3 |
| Major | Inefficient loops (could use `by` or `egen`) | -3 |
| Minor | Inconsistent naming conventions | -1 |
| Minor | Lines exceeding 120 characters | -1 |

## LaTeX Paper (.tex)

| Severity | Issue | Deduction |
|----------|-------|-----------|
| Critical | Compilation failure | -100 |
| Critical | Undefined citation | -15 |
| Critical | Equation error (wrong formula) | -20 |
| Critical | Overfull hbox > 15pt | -10 |
| Major | Typo in prose | -3 |
| Major | Inconsistent notation | -5 |
| Major | Missing table/figure notes | -5 |
| Major | Orphaned cross-references | -5 |
| Minor | Inconsistent citation style (\citet vs \citep) | -1 |
| Minor | Long lines in source | -1 |

## Tables and Figures (output/)

| Severity | Issue | Deduction |
|----------|-------|-----------|
| Critical | Wrong numbers (don't match Stata output) | -30 |
| Major | Missing standard errors or significance stars | -10 |
| Major | Missing N, R-squared, or controls description | -5 |
| Major | Non-publication-quality figure | -10 |
| Major | Missing axis labels or title | -5 |
| Minor | Font size inconsistency across tables | -2 |

## Enforcement

- **Score < 80:** Block commit. List blocking issues.
- **Score < 90:** Allow commit, warn. List recommendations.
- User can override with justification.

## Tolerance Thresholds (Empirical Results)

| Quantity | Tolerance | Rationale |
|----------|-----------|-----------|
| Point estimates | Display precision (3 decimal places) | Journal standard |
| Standard errors | Display precision (3 decimal places) | Journal standard |
| Sample sizes (N) | Exact match | No reason for difference |
| P-values | Same significance level | Exact p may differ by display rounding |
