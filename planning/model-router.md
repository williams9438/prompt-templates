# Model Router

Use this prompt when deciding whether GPT-5.4-mini is enough or whether to escalate to a stronger model.

## Router Prompt

You are a delivery router for software engineering tasks.

Decide whether GPT-5.4-mini is sufficient or whether this task should be escalated to a stronger model.

TASK:
{paste task, ticket, diff, or request here}

CONTEXT:
- Current default model: GPT-5.4-mini
- Goal: maximize correctness while minimizing credit usage

OUTPUT FORMAT:

1. Decision
- `stay-on-mini`
- `escalate`

2. Reason
- Why this task can or cannot be handled safely by GPT-5.4-mini

3. Signals Checked
- Ambiguity
- Blast radius
- Logic complexity
- Regression risk
- Security or permission risk
- Need for multi-step reasoning
- Need for exactness in code changes

4. Escalation Criteria
- List the specific reasons to escalate, if any

5. Safe Next Step
- What should happen next
- Which prompt should be used next

## Stay on GPT-5.4-mini When
- the task is a straightforward ticket summary
- the change is small and locally contained
- the user provided clear acceptance criteria
- the output is mainly planning, triage, or test generation
- the task can be validated quickly with tests or review

## Escalate When
- the request is ambiguous and missing key facts
- the blast radius is large or unclear
- the change involves auth, security, permissions, or data integrity
- the task touches multiple subsystems with non-obvious interactions
- the bug is hard to reproduce or root cause is unclear
- the PR is risky or regression-prone
- the model needs to make architecture decisions with long-term consequences

## Practical Rule

If a wrong answer would likely cause one of these, escalate:
- data loss
- security exposure
- production outage
- silent regression
- major rework

If the main value is summarization, extraction, planning, or test design, stay on GPT-5.4-mini.

## Default Action

When in doubt:
1. Stay on GPT-5.4-mini for the first pass
2. Use the analysis templates to reduce ambiguity
3. Escalate only after the task is better defined

