# Workflow

This file contains the exact prompt chains to use for the most common work types.

## 1. Feature Work

Use this chain when you are building a new capability, changing UX, or extending product behavior.

1. Start with `analysis/ticket-analyzer.md`
2. Then use `analysis/feature-analyzer.md`
3. Then use `planning/implementation-planner.md`
4. Then use `qa/QA-test-generator.md`
5. If the change touches infra or processing, add `analysis/AWS-infra-analyzer.md` or `analysis/processing-analyzer.md`

Recommended flow:
```text
Jira ticket -> ticket analyzer -> feature analyzer -> implementation planner -> QA test generator -> implement -> code review analyzer
```

Use this when:
- the request is primarily about user value
- the scope is broad or ambiguous
- the implementation may affect multiple components

## 2. Bug Fix Work

Use this chain when behavior is broken, a regression appeared, or the user reports an error.

1. Start with `analysis/ticket-analyzer.md`
2. Then use `analysis/bug-analyzer.md`
3. Then use `planning/implementation-planner.md`
4. Then use `qa/QA-test-generator.md`
5. After the fix, use `analysis/code-review-analyzer.md` on the diff or PR

Recommended flow:
```text
Bug report -> ticket analyzer -> bug analyzer -> implementation planner -> QA test generator -> implement fix -> code review analyzer
```

Use this when:
- the issue is a regression or production defect
- you need root-cause thinking before coding
- rollback or mitigation may be needed

## 3. Pull Request Review Work

Use this chain when reviewing a PR, spotting regressions, or deciding if something is release-ready.

1. Start with `analysis/code-review-analyzer.md`
2. If the review finds a real defect, send that finding through `analysis/bug-analyzer.md`
3. If the fix needs work planning, use `planning/implementation-planner.md`
4. If tests are missing, use `qa/QA-test-generator.md`
5. If the PR is tied to a feature or ticket, trace it back to `analysis/ticket-analyzer.md`

Recommended flow:
```text
PR diff -> code review analyzer -> bug analyzer for findings -> implementation planner -> QA test generator
```

Use this when:
- you need to catch correctness issues early
- you want regression spotting before merge
- you are doing release readiness review

## 4. Infra Or Processing Work

Use this chain when the task affects cloud, deployment, pipelines, jobs, queues, storage, or compute-heavy processing.

1. Start with `analysis/ticket-analyzer.md`
2. Then use `analysis/AWS-infra-analyzer.md` or `analysis/processing-analyzer.md`
3. Then use `planning/implementation-planner.md`
4. Then use `qa/QA-test-generator.md`

Recommended flow:
```text
Ticket -> ticket analyzer -> infra or processing analyzer -> implementation planner -> QA test generator
```

## 5. Release Notes

Use this chain when you need to summarize what shipped.

1. Collect the final scope from the ticket, PRs, and planner
2. Use `planning/release-notes.md`
3. Optionally use `analysis/code-review-analyzer.md` if you want release-readiness confirmation

Recommended flow:
```text
Merged work -> release notes -> optional code review check
```

## 6. Incident Review

Use this chain after an outage, failure, or customer-impacting regression.

1. Start with `planning/postmortem.md`
2. If the incident came from a bug, also use `analysis/bug-analyzer.md`
3. If the incident revealed a process gap, update `workflow.md` or the relevant analyzer

Recommended flow:
```text
Incident notes -> postmortem -> bug analyzer if needed -> follow-up implementation planner
```

