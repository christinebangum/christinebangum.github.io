---
name: research-ideation
description: Generate structured research questions, testable hypotheses, and empirical strategies from a topic or dataset
argument-hint: "[topic, phenomenon, or dataset description]"
allowed-tools: ["Read", "Grep", "Glob", "Write"]
---

# Research Ideation

Generate structured research questions, testable hypotheses, and empirical strategies.

**Input:** `$ARGUMENTS` — a topic, phenomenon, or dataset description.

## Steps

1. **Understand the input.** Read `$ARGUMENTS` and any referenced files.

2. **Generate 3-5 research questions** ordered from descriptive to causal:
   - **Descriptive:** What are the patterns?
   - **Correlational:** What factors are associated?
   - **Causal:** What is the effect?
   - **Mechanism:** Why does the effect exist?
   - **Policy:** What are the implications?

3. **For each research question, develop:**
   - **Hypothesis:** A testable prediction with expected sign/magnitude
   - **Identification strategy:** How to establish causality
   - **Data requirements:** What data would be needed?
   - **Key assumptions:** What must hold?
   - **Potential pitfalls:** Threats to identification
   - **Related literature:** 2-3 papers using similar approaches

4. **Rank the questions** by feasibility and contribution.

5. **Save the output** to `quality_reports/research_ideation_[sanitized_topic].md`

## Principles
- Be creative but grounded. Every suggestion must be empirically feasible.
- Think like a referee. For each causal question, identify the identification challenge.
- Consider data availability. A brilliant question with no available data is not actionable.
- Suggest specific datasets where possible.
