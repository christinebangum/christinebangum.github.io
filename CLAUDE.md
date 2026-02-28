# CLAUDE.MD -- Job Market Paper: Charitable Giving as a Luxury Good

**Project:** Is Charitable Giving a Luxury Good?
**Author:** Christine Bangum
**Institution:** BI Norwegian Business School
**Paper repo:** `christinebangum/Single-author` (private, Overleaf-synced)
**Tools:** Stata (analysis), LaTeX via Overleaf (writing)
**Branch:** main

---

## Core Principles

- **Plan first** -- enter plan mode before non-trivial tasks; save plans to `quality_reports/plans/`
- **Verify after** -- check Stata logs and LaTeX compilation at the end of every task
- **Single source of truth** -- Overleaf `.tex` is authoritative for the paper text
- **Quality gates** -- nothing ships below 80/100
- **[LEARN] tags** -- when corrected, save `[LEARN:category] wrong → right` to MEMORY.md
- **Publication-ready** -- all visuals must be polished and journal-quality

---

## Folder Structure (Single-author repo)

```
Single-author/
├── main.tex                     # Paper manuscript (authoritative, Overleaf-synced)
├── *.tex                        # Sections, preamble, appendix
├── *.bib                        # Bibliography
├── code/                        # Stata .do files
│   ├── master.do                # Master script (runs all)
│   ├── 00_setup.do              # Paths, globals, packages
│   ├── 01_clean.do              # Data cleaning
│   ├── 02_sample.do             # Sample construction
│   ├── 03_analysis.do           # Main regressions
│   ├── 04_robustness.do         # Robustness checks
│   └── 05_figures.do            # Figure generation
├── data/                        # (gitignored — confidential admin data)
├── output/
│   ├── tables/                  # .tex table fragments
│   └── figures/                 # .pdf/.png figures
├── literature/                  # Reference papers (PDFs)
├── quality_reports/             # Plans, session logs, specs
├── explorations/                # Research sandbox
└── templates/                   # Workflow templates
```

---

## Commands

```bash
# Stata (run from repo root)
stata-mp -b do code/master.do        # Run full pipeline
stata-mp -b do code/03_analysis.do   # Run single script

# LaTeX (compile local copy for review)
pdflatex -interaction=nonstopmode main.tex
bibtex main
pdflatex -interaction=nonstopmode main.tex
pdflatex -interaction=nonstopmode main.tex
```

---

## Quality Thresholds

| Score | Gate     | Meaning              |
|-------|----------|----------------------|
| 80    | Commit   | Good enough to save  |
| 90    | PR       | Ready for review     |
| 95    | Finalize | Publication-ready    |

---

## Skills Quick Reference

| Command                       | What It Does                              |
|-------------------------------|-------------------------------------------|
| `/compile-latex [file]`       | Compile paper with pdflatex + bibtex      |
| `/proofread [file]`           | Grammar/typo/consistency review           |
| `/review-paper [file]`        | Full manuscript review (referee-style)     |
| `/review-stata [file]`        | Stata code quality review                 |
| `/validate-bib`               | Cross-reference citations vs bibliography |
| `/devils-advocate`            | Challenge identification and arguments    |
| `/lit-review [topic]`         | Literature search + synthesis             |
| `/research-ideation [topic]`  | Research questions + strategies            |
| `/interview-me [topic]`       | Interactive research interview             |
| `/data-analysis [goal]`       | End-to-end Stata analysis workflow        |
| `/commit [msg]`               | Stage, commit, PR, merge                  |
| `/learn [skill-name]`         | Extract discovery into persistent skill   |
| `/context-status`             | Show session health + context usage       |
| `/deep-audit`                 | Repository-wide consistency audit         |

---

## Paper Status

| Section          | Status       | Key Content                                   |
|------------------|--------------|-----------------------------------------------|
| Introduction     | Mid-stage    | Motivation, research question, contribution   |
| Literature       | Mid-stage    | Charitable giving, job displacement, luxury goods |
| Data             | Mid-stage    | Norwegian admin data 2004–2021, tax-deductible donations |
| Empirical Strategy | Mid-stage  | Mass layoffs as exogenous variation            |
| Results          | Mid-stage    | Displacement reduces giving ~2x earnings decline |
| Robustness       | In progress  | Heterogeneity by cause (international aid vs religious) |
| Conclusion       | Draft        | Luxury good characterization, policy implications |
