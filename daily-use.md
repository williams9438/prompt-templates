# Daily Use

Use this as the shortest path from a Jira ticket or PR to a safe engineering outcome.

## What To Paste

Paste as much of this as you have:
- ticket title
- full ticket description
- acceptance criteria
- screenshots, logs, stack traces, or links
- recent related changes
- affected service, screen, job, or endpoint
- constraints, deadlines, or release pressure

If it is a PR review, paste:
- PR description
- diff summary or file list
- test results
- target branch

If it is a bug, paste:
- exact error
- reproduction steps
- expected behavior
- actual behavior
- environment where it happened

## Which Prompt To Use

Use `analysis/ticket-analyzer.md` first for almost everything.

Then choose one of these:
- feature work -> `analysis/feature-analyzer.md`
- bug or regression -> `analysis/bug-analyzer.md`
- processing or batch jobs -> `analysis/processing-analyzer.md`
- AWS or infrastructure -> `analysis/AWS-infra-analyzer.md`
- PR review -> `analysis/code-review-analyzer.md`

Then use:
- `planning/implementation-planner.md` to get the execution order
- `qa/QA-test-generator.md` to define tests before coding
- `planning/model-router.md` if you are not sure GPT-5.4-mini is enough
- `workflow.md` if you want the exact multi-step chain

## Which Session To Run Next

Use this sequence for feature work:
1. `analysis/ticket-analyzer.md`
2. `analysis/feature-analyzer.md`
3. `planning/implementation-planner.md`
4. `qa/QA-test-generator.md`
5. implement
6. `analysis/code-review-analyzer.md`

Use this sequence for bug work:
1. `analysis/ticket-analyzer.md`
2. `analysis/bug-analyzer.md`
3. `planning/implementation-planner.md`
4. `qa/QA-test-generator.md`
5. implement
6. `analysis/code-review-analyzer.md`

Use this sequence for PR review:
1. `analysis/code-review-analyzer.md`
2. if needed, `analysis/bug-analyzer.md`
3. if needed, `planning/implementation-planner.md`
4. if needed, `qa/QA-test-generator.md`

## When To Escalate From GPT-5.4-mini

Stay on GPT-5.4-mini when:
- the task is mainly summarization, extraction, planning, or test design
- the scope is small and local
- the acceptance criteria are clear
- the answer can be validated quickly

Escalate when:
- the request is ambiguous
- the blast radius is large
- the task affects auth, security, permissions, or data integrity
- the bug is hard to reproduce
- the PR touches multiple subsystems
- a wrong answer would cause outage, data loss, silent regression, or major rework

## Simple Rule

If you can reduce risk with more context, do that first.
If the remaining uncertainty is still high after analysis, escalate.

## Daily Loop

1. Paste the ticket, bug, or PR context.
2. Run the right analyzer.
3. Run the planner.
4. Run the QA checklist.
5. Implement the smallest safe change.
6. Run code review on the result.
7. Escalate only when the task is still too risky for mini.

