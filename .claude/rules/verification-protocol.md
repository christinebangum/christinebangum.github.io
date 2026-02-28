# Task Completion Verification Protocol

**At the end of EVERY task, Claude MUST verify the output works correctly.** This is non-negotiable.

## For Stata Scripts (.do):
1. Run the script: `stata-mp -b do code/script_name.do`
2. Check the Stata log file for errors: `grep -i "error\|r([0-9]*)" script_name.log`
3. Verify output files (tables, figures) were created with non-zero size
4. Spot-check key estimates for reasonable magnitude
5. Confirm sample sizes match expectations

## For LaTeX Paper (.tex):
1. Compile with 3-pass sequence:
   ```bash
   pdflatex -interaction=nonstopmode main.tex
   bibtex main
   pdflatex -interaction=nonstopmode main.tex
   pdflatex -interaction=nonstopmode main.tex
   ```
2. Check for compilation errors in the log
3. Grep for overfull hbox warnings: `grep "Overfull" main.log`
4. Grep for undefined citations: `grep "undefined" main.log`
5. Verify PDF was created successfully

## For Table Fragments (.tex output):
1. Verify the .tex file is valid LaTeX (can be included via `\input{}`)
2. Check that numbers match the Stata log output
3. Confirm standard errors, significance stars, and notes are present

## For Figures (.pdf/.png output):
1. Verify file exists with non-zero size
2. Read/view the figure to confirm it renders correctly
3. Check resolution (should be publication-quality)
4. Verify axis labels, titles, and legends are present and readable

## Common Pitfalls:
- **Stata path errors**: Always use globals from master.do, never hardcoded paths
- **Missing packages**: Check that required Stata packages are installed (`ssc install`)
- **Encoding issues**: Norwegian characters in data — ensure UTF-8 handling
- **Assuming success**: Always check the log file, even if Stata exits without visible error

## Verification Checklist:
```
[ ] Script/compilation runs without errors
[ ] Output files created successfully
[ ] Key results are reasonable in magnitude
[ ] Sample sizes match expectations
[ ] No undefined citations or broken references
[ ] Reported results to user
```
