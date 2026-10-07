# Pre-Implementation Critical Review

Use this prompt before starting implementation work. Its purpose is to challenge the proposed solution against the current codebase before any code is written.

## Input

Task:
[Paste the Jira ticket, requirement, bug report, proposed solution, PR context, or implementation idea here]

Repository / codebase context:
[Paste relevant files, architecture notes, branch/environment details, recent commits, or instruct the model to inspect the codebase directly]

## Instructions

Do not start coding yet.

Inspect the existing codebase before making recommendations. Do not review the proposal in isolation.

### 1. What problem are we actually trying to solve?

- Restate the problem in simple terms.
- Separate the root problem from the proposed implementation.
- Identify whether the proposal solves the cause or only the symptom.

### 2. What is the proposed solution?

- Explain how it would work.
- List the assumptions it depends on.
- Identify implicit architectural or operational assumptions.

### 3. What are the drawbacks of this solution?

Consider technical debt, complexity, maintainability, duplicated data or logic, stale data, performance, scalability, security, permissions, user experience, operational burden, observability, support/debugging cost, and future migration cost.

### 4. What problems could arise when compared with the CURRENT CODEBASE?

Inspect the current implementation before answering.

Identify:
- existing patterns this solution conflicts with
- duplicate functionality already present
- older assumptions this could break
- components depending on the code being changed
- hidden coupling between modules
- shared state that could be affected
- overlapping database models or fields
- API inconsistencies
- frontend/backend contract mismatches
- worker/background-job dependencies
- cache/state synchronization issues
- permission or authorization differences
- feature-flag interactions
- environment-specific behaviour
- backwards-compatibility problems
- tests that reveal behaviour that must be preserved
- recent changes this could overwrite or regress
- branch/release-history differences that may make the change unsafe to promote

Answer explicitly:
- Does the current codebase already solve part of this problem?
- Would this create a second way of doing the same thing?
- Would this introduce a new source of truth?
- Which existing code paths could behave differently?
- Which files/modules are most likely to conflict?
- Are there existing abstractions we should reuse?
- Does this violate established architecture or conventions?
- Are there recent changes in the same area that could regress?
- Could this behave differently in Dev, Staging, or Production?
- Could this make future merges, hotfixes, rollbacks, or releases harder?
- Is it compatible with the current deployed Production state, not just Dev?

### 5. What are the edge cases?

Consider create, update, delete, retry, duplicate requests, partial failure, timeout, network failure, stale state, concurrent users/processes, missing data, invalid data, very large datasets, old records, and mixed-version deployments.

### 6. What happens when something fails halfway through?

- What state is left behind?
- Can the operation safely be retried?
- Is it idempotent?
- Could it create duplicate or inconsistent records?
- Could it leave orphaned files, rows, jobs, or external resources?
- Is cleanup required?
- How would we detect and recover from the partial state?

### 7. What existing functionality could this regress?

Identify affected components, APIs, database models, workflows, permissions, background workers, UI state, integrations, caches, event handlers, feature flags, tests, and deployment/runtime configuration.

Separate direct regressions from indirect/blast-radius risks.

### 8. What are the data consistency risks?

- What becomes the source of truth?
- Could two representations become out of sync?
- What happens when the original record is changed or deleted?
- What happens if an associated file/object exists but the database record does not, or vice versa?
- What happens during retries or concurrent writes?
- Are snapshots/versioning required?

### 9. What are the deployment and branch risks?

Consider Dev, Staging, Production, branch ancestry/divergence, hotfixes not merged back, migrations, environment variables, feature flags, workers/services, backwards compatibility, mixed-version deployments, deployment ordering, and rollback compatibility.

Answer:
- Does this require a specific promotion order?
- Is there code already in Production that is not in Dev/Staging?
- Could merging/cherry-picking overwrite environment-specific fixes?
- What must be reconciled before implementation or release?

### 10. What is the rollback strategy?

- Can this change be reverted safely?
- Will rollback leave incompatible database records or files?
- Will previously created data still work?
- Are migrations reversible?
- Can the feature be disabled independently?
- What happens to in-flight jobs or partially completed work?

### 11. Are there simpler alternatives?

Give at least two alternatives where reasonable.

For each explain:
- how it works
- advantages
- disadvantages
- codebase fit
- implementation complexity
- operational complexity
- migration/release impact
- failure/recovery characteristics

Do not recommend the original proposal automatically.

### 12. Compare the options

| Approach | Benefits | Drawbacks | Codebase Fit | Regression Risk | Complexity | Rollback | Recommended Use Case |
|---|---|---|---|---|---|---|---|

### 13. What would you recommend?

Choose one approach and explain why. Prefer reuse of existing abstractions, one source of truth, small reversible changes, compatibility with current code paths, predictable failure/retry behaviour, minimal branch/release complexity, and explicit rollback.

### 14. What should be verified before implementation?

List:
- code areas to inspect
- assumptions to confirm
- Production/Staging differences
- dependent services or workers
- data/migration state
- feature flags/configuration
- recent related commits/PRs
- existing tests to read first

### 15. What tests should exist?

Include unit, integration, regression, failure-path, retry/idempotency, permission, concurrency, migration/backwards-compatibility, environment/configuration, and manual acceptance tests where applicable.

### 16. Define implementation boundaries

Clearly state:
- what should change
- what should NOT change
- what existing behaviour must be preserved
- which components are explicitly out of scope
- which dependencies must not be rewritten unless proven necessary

### 17. Final risk assessment

Provide:
- Risk: Low / Medium / High
- Main reason
- Biggest unknown
- Biggest potential regression
- Biggest incompatibility with the current codebase
- Biggest operational/release risk

## Required Ending

### CURRENT CODEBASE CONFLICTS
[List the main problems this solution could create in the existing system]

### RECOMMENDATION
[Recommended approach]

### DO NOT IMPLEMENT YET
[List anything that must be confirmed first]

### SAFE TO IMPLEMENT WHEN
[List the conditions that should be true before coding starts]
