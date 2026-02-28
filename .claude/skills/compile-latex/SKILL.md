---
name: compile-latex
description: Compile the LaTeX paper with pdflatex (3 passes + bibtex). Use when checking paper compilation locally.
argument-hint: "[filename without .tex extension, default: main]"
allowed-tools: ["Read", "Bash", "Glob"]
---

# Compile LaTeX Paper

Compile the paper using pdflatex with full citation resolution.

## Steps

1. **Compile with 3-pass sequence:**

```bash
pdflatex -interaction=nonstopmode $ARGUMENTS.tex
bibtex $ARGUMENTS
pdflatex -interaction=nonstopmode $ARGUMENTS.tex
pdflatex -interaction=nonstopmode $ARGUMENTS.tex
```

If no `$ARGUMENTS` provided, default to `main`.

2. **Check for warnings:**
   - Grep output for `Overfull \\hbox` warnings
   - Grep for `undefined citations` or `Label(s) may have changed`
   - Report any issues found

3. **Report results:**
   - Compilation success/failure
   - Number of overfull hbox warnings
   - Any undefined citations
   - PDF page count

## Why 3 passes?
1. First pdflatex: Creates `.aux` file with citation keys
2. bibtex: Reads `.aux`, generates `.bbl` with formatted references
3. Second pdflatex: Incorporates bibliography
4. Third pdflatex: Resolves all cross-references with final page numbers

## Important
- Check whether the project uses `bibtex` or `biber` and adjust accordingly
- If using xelatex instead of pdflatex, swap the command
