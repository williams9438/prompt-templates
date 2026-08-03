# Agent Policy

This file combines routing rules, session boundaries, and review standards for everyday engineering work.

## 1. Default Model Policy

Use GPT-5.4-mini by default for:
- summarization
- extraction
- planning
- test design
- routine code review

Escalate to a stronger model when:
- the task is ambiguous
- the change is high risk
- the blast radius is large
- the task touches security, auth, permissions, or data integrity
- the bug is hard to reproduce
- the answer could easily create a regression or outage

## 2. Session Policy

Use a fresh session for:
- independent bug investigation
- independent regression review
- final verification
- release review
- review-finding resolution when the findings must be rechecked cleanly

Reuse the same session only when:
- the task is low risk
- the task is primarily summarization or planning
- the next step depends directly on the current step and does not need independence

## 3. Review Standards

All reviews should check:
- correctness
- missing tests
- regression risk
- error handling
- cleanup and teardown safety
- release readiness

Treat `try/finally` or equivalent cleanup as the default expectation whenever code acquires resources, mutates state, or must guarantee cleanup after failure.

## 4. Evidence Standards

The model should:
- separate facts from assumptions
- state what is confirmed versus inferred
- report exact tests run
- state what was not verified
- avoid claiming completion too early

## 5. Safe Workflow

1. Analyze the ticket or PR
2. Decide whether mini is enough
3. Escalate only if risk remains high
4. Use a fresh session for independent review
5. Verify with tests before claiming completion

## 6. Operational Rule

If the task can be solved with more context instead of a stronger model, gather the context first.
If the task remains risky after analysis, escalate.
If the task requires independent judgment, use a fresh session.

