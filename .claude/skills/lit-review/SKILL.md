---
name: lit-review
description: Structured literature search and synthesis with citation extraction and gap identification
argument-hint: "[topic, paper title, or research question]"
allowed-tools: ["Read", "Grep", "Glob", "Write", "WebSearch", "WebFetch"]
---

# Literature Review

Conduct a structured literature search and synthesis on the given topic.

**Input:** `$ARGUMENTS` — a topic, paper title, research question, or phenomenon to investigate.

## Steps

1. **Parse the topic** from `$ARGUMENTS`.

2. **Search for related work** using available tools:
   - Check `literature/` for uploaded papers
   - Use `WebSearch` to find recent publications
   - Read any existing `.bib` file for papers already in the project

3. **Organize findings** into these categories:
   - **Theoretical contributions** — models, frameworks, mechanisms
   - **Empirical findings** — key results, effect sizes, data sources
   - **Methodological innovations** — estimators, identification strategies
   - **Open debates** — unresolved disagreements

4. **Identify gaps and opportunities:**
   - What questions remain unanswered?
   - What data or methods could address them?
   - Where do findings conflict?

5. **Extract citations** in BibTeX format for all papers discussed.

6. **Save the report** to `quality_reports/lit_review_[sanitized_topic].md`

## Output Format

```markdown
# Literature Review: [Topic]

**Date:** [YYYY-MM-DD]
**Query:** [Original query]

## Summary
[2-3 paragraph overview]

## Key Papers

### [Author (Year)] — [Short Title]
- **Main contribution:** [1-2 sentences]
- **Method:** [Identification strategy / data]
- **Key finding:** [Result with effect size if available]
- **Relevance:** [Why it matters for our research]

## Thematic Organization
### Theoretical Contributions
### Empirical Findings
### Methodological Innovations

## Gaps and Opportunities
1. [Gap 1]
2. [Gap 2]

## BibTeX Entries
```

## Important
- **Do NOT fabricate citations.** If you're unsure about a paper's details, flag it for verification.
- Prioritize recent work (last 5-10 years) unless seminal papers are older.
- Note working papers vs published papers.
