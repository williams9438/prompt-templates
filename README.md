# prompt-templates

An opinionated library of prompts for turning raw requests into safe, implementation-ready engineering work.

This repo is designed to help you:
- turn feature requests into clear engineering specs
- debug and fix bugs with less guesswork
- split Jira tickets into parallelizable work
- improve test coverage and regression safety
- reason about processing, infrastructure, and AWS impact before code is written

## How To Use This Repo

Use the templates as a workflow, not as isolated prompts.

Recommended sequence:
1. Start with `analysis/ticket-analyzer.md` for any Jira ticket or ambiguous request.
2. Use `analysis/feature-analyzer.md` for product features or UX changes.
3. Use `analysis/bug-analyzer.md` for defects, regressions, incidents, or unexpected behavior.
4. Use `analysis/processing-analyzer.md` for batch jobs, pipelines, data workflows, or long-running compute.
5. Use `analysis/AWS-infra-analyzer.md` for cloud, deployment, IAM, scaling, or operational changes.
6. Use `analysis/code-review-analyzer.md` for PR review, regression spotting, and release readiness.
7. Use `qa/QA-test-generator.md` once the task is understood to produce a strong validation plan.
8. Use `planning/implementation-planner.md` to turn the analysis into an execution sequence.
9. Use `planning/release-notes.md` or `planning/postmortem.md` when you need a delivery summary or incident write-up.
10. Use `workflow.md` for exact prompt chains and `planning/model-router.md` when deciding whether to stay on GPT-5.4-mini.
11. Use `planning/multi-session-workflow-designer.md` to rewrite a one-off prompt into a seven-session engineering workflow.

## Operating Principles

These prompts are written to push the model toward industrial-grade output:
- separate confirmed facts from assumptions
- expose missing information early
- identify dependency order and parallelizable work
- call out edge cases, regressions, and rollback concerns
- include testing and validation, not just implementation ideas
- avoid code generation unless explicitly requested

## Daily Jira Workflow

For day-to-day ticket work, use this loop:
1. Paste the Jira ticket into `analysis/ticket-analyzer.md`.
2. If the ticket is a bug, use `analysis/bug-analyzer.md` instead or after `analysis/ticket-analyzer.md`.
3. Ask the model to highlight open questions, risks, and scope boundaries.
4. Use `planning/implementation-planner.md` to get an ordered task list.
5. Use `qa/QA-test-generator.md` to define test coverage before coding.
6. Implement the smallest safe change.
7. Re-run the relevant analysis prompt on any follow-up tickets or regression concerns.

This workflow reduces:
- missed dependencies
- accidental scope creep
- regression risk
- vague Jira updates
- late discovery of test gaps

## What To Include In Your Input

The quality of the output depends heavily on the context you paste in.

Try to include:
- the ticket title and full description
- acceptance criteria
- screenshots, logs, error messages, or links
- affected environment or service
- known constraints
- deadline or urgency if relevant
- what changed recently, if this is a regression

## Template Index

- `analysis/ticket-analyzer.md` - general Jira ticket to implementation-ready specification
- `analysis/feature-analyzer.md` - product feature analysis and architecture planning
- `analysis/bug-analyzer.md` - defect analysis, reproduction, likely root cause, and fix strategy
- `analysis/processing-analyzer.md` - data and processing pipeline analysis
- `analysis/AWS-infra-analyzer.md` - infrastructure and operations analysis
- `analysis/code-review-analyzer.md` - PR review and regression spotting
- `qa/QA-test-generator.md` - test strategy and validation planning
- `planning/implementation-planner.md` - task sequencing, dependencies, and rollout planning
- `planning/release-notes.md` - delivery summary and user-facing change log
- `planning/postmortem.md` - incident review and corrective action planning
- `planning/model-router.md` - decide when GPT-5.4-mini is enough vs when to escalate
- `workflow.md` - exact prompt chains for feature, bug, PR, infra, release, and incident work
- `qa/jira-eval-checklist.md` - reusable daily Jira quality checklist
- `planning/multi-session-workflow-designer.md` - rewrite prompt into an evidence-driven multi-session workflow

## Best Practices For Optimum Results

- Keep requests specific and single-purpose when possible.
- Paste the exact ticket or issue text instead of paraphrasing.
- Ask for one output at a time when the task is large.
- Tell the model which part of the system is in scope and what is out of scope.
- Use the analysis outputs as working documents before you start coding.
- Prefer small, reversible changes and test them early.

## Suggested Prompt Chain

For a feature:
`analysis/ticket-analyzer.md` -> `analysis/feature-analyzer.md` -> `planning/implementation-planner.md` -> `qa/QA-test-generator.md`

For a bug:
`analysis/ticket-analyzer.md` -> `analysis/bug-analyzer.md` -> `planning/implementation-planner.md` -> `qa/QA-test-generator.md`

For infra or pipeline work:
`analysis/ticket-analyzer.md` -> `analysis/AWS-infra-analyzer.md` or `analysis/processing-analyzer.md` -> `planning/implementation-planner.md` -> `qa/QA-test-generator.md`

## Repo Goal

This repository is intended to be your personal AI engineering cockpit:
- faster ticket triage
- clearer specs
- safer implementation
- fewer regressions
- stronger daily execution
