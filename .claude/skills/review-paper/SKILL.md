---
name: review-paper
description: Comprehensive manuscript review covering argument structure, identification strategy, econometric specification, citation completeness, and potential referee objections. Use for referee-style feedback on the JMP.
argument-hint: "[paper filename or path to .tex/.pdf]"
allowed-tools: ["Read", "Grep", "Glob", "Write", "Agent"]
---

# Manuscript Review

Produce a thorough, constructive review — the kind of report a top-journal referee would write.

**Input:** `$ARGUMENTS` — path to the paper (.tex or .pdf).

## Steps

1. **Locate and read the manuscript.** Read the full paper end-to-end. For long PDFs, read in chunks (5 pages at a time).

2. **Evaluate across 6 dimensions** (see below).

3. **Generate 3-5 "referee objections"** — the tough questions a top referee would ask.

4. **Produce the review report.**

5. **Save to** `quality_reports/paper_review_[sanitized_name].md`

## Review Dimensions

### 1. Argument Structure
- Is the research question clearly stated?
- Does the introduction motivate the question effectively?
- Is the logical flow sound (question → method → results → conclusion)?
- Are the conclusions supported by the evidence?

### 2. Identification Strategy
- Is the causal claim credible?
- What are the key identifying assumptions? Are they stated explicitly?
- Are there threats to identification (omitted variables, reverse causality, measurement error)?
- Are robustness checks adequate?

### 3. Econometric Specification
- Correct standard errors (clustered? robust? bootstrap?)?
- Appropriate functional form?
- Sample selection issues?
- Are point estimates economically meaningful (not just statistically significant)?

### 4. Literature Positioning
- Are the key papers cited?
- Is prior work characterized accurately?
- Is the contribution clearly differentiated from existing work?

### 5. Writing Quality
- Clarity and concision
- Academic tone
- Consistent notation throughout
- Abstract effectively summarizes the paper

### 6. Presentation
- Are tables and figures well-designed?
- Is notation consistent throughout?
- Are there any typos or formatting issues?

## Output Format

```markdown
# Manuscript Review: [Paper Title]

## Summary Assessment
**Overall recommendation:** [Strong Accept / Accept / R&R / Reject]
[2-3 paragraph summary]

## Strengths
1. [Strength 1]
2. [Strength 2]

## Major Concerns
### MC1: [Title]
- **Dimension:** [Identification / Econometrics / etc.]
- **Issue:** [Description]
- **Suggestion:** [How to address]

## Minor Concerns
### mc1: [Title]
- **Issue:** [Description]
- **Suggestion:** [Fix]

## Referee Objections
### RO1: [Question]
**Why it matters:** [Why this could be fatal]
**How to address it:** [Suggested response]

## Summary Ratings
| Dimension | Rating (1-5) |
|-----------|-------------|
| Argument Structure | [N] |
| Identification | [N] |
| Econometrics | [N] |
| Literature | [N] |
| Writing | [N] |
| Presentation | [N] |
```

## Principles
- Be constructive. Every criticism should come with a suggestion.
- Be specific. Reference exact sections, equations, tables.
- Think like a referee at a top-5 journal.
- Distinguish fatal flaws from minor issues.
- Do NOT fabricate details.
