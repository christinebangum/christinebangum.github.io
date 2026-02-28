---
name: devils-advocate
description: Challenge the paper's identification strategy, arguments, and presentation with 5-7 tough questions. Adopts a skeptical referee perspective.
argument-hint: "[section name or 'full paper']"
allowed-tools: ["Read", "Grep", "Glob"]
---

# Devil's Advocate Review

Critically examine the paper and challenge its arguments with 5-7 specific, tough questions.

**Philosophy:** "We arrive at the strongest possible paper through active challenge."

## Setup

1. **Read the target file(s)** (the paper section or full paper being challenged)
2. **Read the knowledge base** in `.claude/rules/knowledge-base-template.md` for context
3. **Understand the identification strategy** before challenging it

## Challenge Categories

Generate 5-7 challenges from these categories:

### 1. Identification Challenges
> "What if mass layoffs are correlated with regional economic shocks that independently affect giving?"

### 2. Alternative Explanation Challenges
> "Could the decline in giving reflect changes in solicitation rather than income effects?"

### 3. Measurement Challenges
> "Tax-deductible donations only capture formal giving. What about informal transfers?"

### 4. External Validity Challenges
> "Norway's welfare state may buffer displaced workers. Would results generalize?"

### 5. Specification Challenges
> "Why this functional form? What happens with alternative specifications?"

### 6. Literature Positioning Challenges
> "How does this differ from [related paper]? Is the contribution clear enough?"

### 7. Presentation Challenges
> "The abstract promises X, but the evidence mainly shows Y."

## Output Format

```markdown
# Devil's Advocate: [Section/Paper Title]

## Challenges

### Challenge 1: [Category] — [Short title]
**Question:** [The specific question]
**Why it matters:** [What could go wrong / why a referee would care]
**Suggested response:** [How to address it in the paper]
**Severity:** [High / Medium / Low]

[Repeat for 5-7 challenges]

## Summary Verdict
**Strengths:** [2-3 things done well]
**Critical to address:** [0-2 must-fix items]
**Would strengthen:** [2-3 improvements]
```

## Principles
- Be specific: reference exact claims, tables, and specifications
- Be constructive: every challenge has a suggested response
- Think like a hostile but fair referee
- Prioritize identification threats over presentation issues
