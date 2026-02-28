---
name: review-stata
description: Run the Stata code review protocol on .do files. Checks code quality, reproducibility, domain correctness, and professional standards. Produces a report without editing files.
argument-hint: "[filename or 'all']"
allowed-tools: ["Read", "Grep", "Glob", "Write", "Agent"]
---

# Review Stata Scripts

Run a comprehensive Stata code review protocol.

## Steps

1. **Identify scripts to review:**
   - If `$ARGUMENTS` is a specific `.do` filename: review that file only
   - If `$ARGUMENTS` is `all`: review all .do files in `code/`

2. **For each script, launch the `stata-reviewer` agent** to check:

### Review Categories

#### 1. SCRIPT STRUCTURE & HEADER
- [ ] Header with title, author, purpose, inputs, outputs
- [ ] `clear all` and `set more off` at top
- [ ] Sections clearly labeled with comments
- [ ] Logical flow (setup → load → clean → analyze → output)

#### 2. REPRODUCIBILITY
- [ ] `set seed` for any stochastic operations
- [ ] All paths use globals (no hardcoded absolute paths)
- [ ] Output directories created if needed
- [ ] Package dependencies documented (`ssc install` requirements)

#### 3. DATA MANAGEMENT
- [ ] Merge assertions (`assert _merge == 3` or documented handling)
- [ ] Sort stability (`sort varlist, stable` when order matters)
- [ ] Missing value handling documented
- [ ] Variable labels applied to generated variables
- [ ] Sample restrictions clearly documented

#### 4. ESTIMATION
- [ ] Correct clustering of standard errors
- [ ] Factor variable base categories explicit (`ib#.varname`)
- [ ] Estimation sample documented (N, restrictions)
- [ ] Multiple specifications for robustness
- [ ] Point estimates checked for reasonable magnitude

#### 5. OUTPUT QUALITY
- [ ] Tables exported with `esttab`/`estout` in .tex format
- [ ] Figures exported as .pdf at publication quality
- [ ] Axis labels, titles, legends present and readable
- [ ] Standard errors and significance indicators included
- [ ] Notes explaining controls, sample, clustering

#### 6. CONFIDENTIALITY
- [ ] No individual-level data displayed
- [ ] Cell counts above minimum threshold
- [ ] No data files committed to git

3. **Save report** to `quality_reports/[script_name]_stata_review.md`

4. **Present summary:**
   - Total issues per script
   - Breakdown by severity (Critical / High / Medium / Low)

5. **IMPORTANT: Do NOT edit any source files.** Only produce reports.
