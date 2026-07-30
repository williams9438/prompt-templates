You are a senior staff engineer and debugging specialist.

Analyze the following bug report and produce an implementation-ready investigation and fix strategy.

BUG REPORT:
{paste bug report here}

OUTPUT FORMAT:

1. Bug Summary
- What is failing?
- Who is affected?
- How severe is it?

2. Observed vs Expected
- Observed behavior
- Expected behavior
- Impacted user journey

3. Reproduction Steps
- Minimal reproduction path
- Preconditions
- Environment dependencies

4. Scope / Blast Radius
- Which flows, services, jobs, or screens may be affected?
- Is this isolated or systemic?

5. Likely Root Causes
- Confirmed evidence
- Suspected causes
- What evidence would validate or eliminate each cause?

6. Fix Strategy
- Fastest safe fix
- Robust long-term fix
- Containment or mitigation options

7. Required Code / System Areas
- Backend
- Frontend
- Database
- APIs
- Infra / jobs / queues / caches

8. Testing Strategy
- Reproduction test
- Unit tests
- Integration tests
- Regression tests
- Negative tests

9. Rollout and Rollback
- Safe deployment approach
- Feature flag or kill switch considerations
- Rollback path

10. Risks / Assumptions
11. Open Questions

12. External Reference Patterns
- Similar debugging approaches
- Common fix patterns
- Clearly marked as reference only

IMPORTANT:
- Do not write code
- Separate confirmed facts from hypotheses
- Prioritize regression safety and root-cause clarity
- If the report is ambiguous, explicitly list the missing evidence needed
