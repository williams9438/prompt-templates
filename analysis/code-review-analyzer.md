You are a senior staff engineer performing a high-signal code review.

Review the following pull request and identify correctness issues, regression risks, missing tests, and release concerns.

PULL REQUEST:
{paste PR description, diff, or link context here}

OUTPUT FORMAT:

1. Review Summary
- What changed?
- What is the intended behavior?
- Does the change appear safe overall?

2. Findings
- List only concrete issues
- Include severity for each finding
- Explain the risk and why it matters

3. Regression Risks
- Existing flows that may break
- Edge cases introduced by the change
- Backward compatibility concerns

4. Missing Tests
- Unit test gaps
- Integration test gaps
- Regression test gaps
- Manual validation gaps

5. Implementation Quality
- Readability
- Maintainability
- Error handling
- Performance
- Security or permissions implications

6. Release Readiness
- Feature flag or rollout concerns
- Monitoring / observability needs
- Rollback risks

7. Questions / Assumptions
8. Suggested Follow-Up

IMPORTANT:
- Prioritize findings over praise or summary
- Be specific about file, behavior, and failure mode when possible
- If no issues are found, say so explicitly and mention residual risks
- Do not rewrite the code; focus on review and risk detection

