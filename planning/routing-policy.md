# Routing Policy

Use this policy to decide whether a task should stay on GPT-5.4-mini or escalate to a stronger model.

## Default

Start with GPT-5.4-mini for:
- ticket triage
- ticket summarization
- requirement extraction
- implementation planning
- test planning
- routine PR review
- release note drafting

## Escalate to a stronger model when:
- the task is ambiguous after the first pass
- the problem affects auth, security, permissions, or data integrity
- the blast radius is broad or hard to predict
- the bug is hard to reproduce or root cause is unclear
- the implementation spans multiple subsystems
- the task needs architecture decisions with long-term consequences
- a wrong answer could cause outage, data loss, silent regression, or major rework

## Stay on GPT-5.4-mini when:
- the task is mostly summarization, extraction, planning, or test design
- the scope is local and constrained
- acceptance criteria are clear
- the output can be validated quickly with tests or review

## Escalation Rule

If more context could materially reduce the risk, gather that context first.
If the task is still uncertain or high-impact after analysis, escalate.

## Practical Routing Order

1. Run the relevant analyzer
2. Check the output against this policy
3. Escalate only if the remaining uncertainty or risk is still high
4. Use a fresh session for independent review stages

