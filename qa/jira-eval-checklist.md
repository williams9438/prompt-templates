# Jira Eval Checklist

Use this checklist to score how good the AI output is for a daily Jira ticket.

## 1. Ticket Understanding
- Did the model restate the request accurately?
- Did it identify whether this is a feature, bug, infra item, or mixed work?
- Did it separate facts from assumptions?

## 2. Scope Control
- Did it call out what is in scope?
- Did it call out what is out of scope?
- Did it mention any missing information that could change the implementation?

## 3. Risk Detection
- Did it list regression risks?
- Did it identify edge cases?
- Did it mention rollout or rollback concerns when relevant?

## 4. Dependency Awareness
- Did it identify backend, frontend, database, API, infra, or external dependencies?
- Did it show the right order of work?
- Did it expose any blockers?

## 5. Implementation Quality
- Did it suggest a small, safe first step?
- Did it avoid overengineering?
- Did it keep parallel work separate from dependent work?

## 6. Test Quality
- Did it include unit tests?
- Did it include integration tests if the system boundary is affected?
- Did it include regression tests for known failure paths?
- Did it include the highest-risk user flows?

## 7. Output Usability
- Could an engineer act on the output immediately?
- Did it use clear sections and short labels?
- Did it avoid vague language like "maybe", "probably", or "should consider" without justification?

## 8. Daily Jira Scoring

Score each category from 0 to 2:
- 0 = missing
- 1 = partial
- 2 = strong

Target total:
- 12 to 16 = acceptable for routine work
- 17 to 20 = strong enough to implement with low ambiguity
- below 12 = rerun with more context or escalate to a stronger model

## 9. Minimum Re-run Triggers

Rerun the analysis or escalate if any of these happen:
- the output invents requirements not present in the ticket
- the output misses a likely regression path
- the output cannot explain how to test the change
- the output changes scope without calling it out
- the output feels correct but is too vague to implement safely

## 10. Ticket Inputs To Always Include
- ticket title
- full description
- acceptance criteria
- screenshots or logs
- related links
- recent changes
- environment or service name
- known constraints

