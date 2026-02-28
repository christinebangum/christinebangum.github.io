---
name: validate-bib
description: Validate bibliography entries against citations in the paper. Find missing entries and unused references.
allowed-tools: ["Read", "Grep", "Glob"]
---

# Validate Bibliography

Cross-reference all citations in the paper against bibliography entries.

## Steps

1. **Read the bibliography file** (.bib) and extract all citation keys

2. **Scan all .tex files for citation keys:**
   - Look for `\cite{`, `\citet{`, `\citep{`, `\citeauthor{`, `\citeyear{`, `\citealt{`
   - Extract all unique citation keys used

3. **Cross-reference:**
   - **Missing entries:** Citations used in paper but NOT in bibliography
   - **Unused entries:** Entries in bibliography not cited anywhere
   - **Potential typos:** Similar-but-not-matching keys (e.g., `Smith2020` vs `smith2020`)

4. **Check entry quality** for each bib entry:
   - Required fields present (author, title, year, journal/booktitle)
   - Author field properly formatted
   - Year is reasonable
   - No malformed characters or encoding issues

5. **Report findings:**
   - List of missing bibliography entries (CRITICAL)
   - List of unused entries (informational)
   - List of potential typos in citation keys
   - List of quality issues

## Files to scan:
```
**/*.tex
**/*.bib
```
