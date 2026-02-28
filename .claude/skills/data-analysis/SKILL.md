---
name: data-analysis
description: End-to-end Stata data analysis workflow from exploration through regression to publication-ready tables and figures
argument-hint: "[dataset description or analysis goal]"
allowed-tools: ["Read", "Grep", "Glob", "Write", "Edit", "Bash", "Agent"]
---

# Data Analysis Workflow (Stata)

Run an end-to-end data analysis in Stata: load, explore, analyze, and produce publication-ready output.

**Input:** `$ARGUMENTS` — a description of the analysis goal (e.g., "regress donations on displacement with individual fixed effects").

## Constraints

- **All paths relative** using globals set in master.do
- **Save all output** to `output/tables/` and `output/figures/`
- **Publication-quality figures** — white background, journal-appropriate fonts/sizes
- **Run review-stata** on the generated script before presenting results
- **Confidential data** — never display individual-level data or small cell counts

## Workflow Phases

### Phase 1: Setup and Data Loading

1. Create Stata .do file with proper header:
   ```stata
   /*==============================================================================
   Title:    [Descriptive Title]
   Author:   Christine Bangum
   Purpose:  [What this script does]
   Input:    [Data files]
   Output:   [Figures, tables]
   ==============================================================================*/

   * 0. Setup
   clear all
   set more off
   set seed 12345

   * Paths (set in master.do or here)
   global root  "."
   global data  "$root/data"
   global code  "$root/code"
   global output "$root/output"
   ```

2. Load and inspect the dataset

### Phase 2: Exploratory Data Analysis

Generate diagnostic outputs:
- **Summary statistics:** `summarize`, `tabulate`, missingness
- **Distributions:** `histogram` for key continuous variables
- **Relationships:** `correlate`, scatter plots
- **Time patterns:** If panel data, plot trends over time
- **Group comparisons:** If treatment/control, compare pre-treatment means

### Phase 3: Main Analysis

Based on the research question:
- **Regression analysis:** `reghdfe` for high-dimensional FE, `xtreg` for standard panel
- **Standard errors:** Cluster at the appropriate level (document why)
- **Multiple specifications:** Start simple, progressively add controls
- **Effect sizes:** Report standardized effects alongside raw coefficients

### Phase 4: Publication-Ready Output

**Tables:**
- Use `esttab`/`estout` for regression tables
- Export as `.tex` for LaTeX inclusion
- Include all standard elements: coefficients, SEs, significance stars, N, R-squared

**Figures:**
- Use `graph twoway` or `coefplot` with clean styling
- Export as `.pdf` for high quality
- Include proper axis labels, titles, legends

### Phase 5: Save and Review

1. Run the review-stata agent on the generated script
2. Address any Critical or High issues

## Important

- **Reproduce, don't guess.** If the user specifies a regression, run exactly that.
- **Show your work.** Print summary statistics before regression.
- **No hardcoded values.** Use globals for sample restrictions, date ranges, etc.
- **Check for issues.** Multicollinearity, outliers, sample restrictions.
