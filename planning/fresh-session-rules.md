# Fresh Session Rules

Use a new Codex session for stages that must be independent from earlier reasoning.

## Must Be Fresh

Always use a fresh session for:
- independent bug investigation
- independent regression review
- final verification before merge
- release-level regression review
- incident postmortem if you want a clean read
- review-finding resolution when the reviewer findings must be revalidated independently

## Should Usually Be Fresh

Prefer a fresh session for:
- PR review after implementation
- QA review of the final branch
- code review of a hotfix
- release readiness checks

## Can Reuse the Same Session

It is usually fine to reuse the same session for:
- one-pass ticket summarization
- implementation planning
- test plan generation
- release note drafting
- status updates

## Why Fresh Matters

A fresh session helps prevent:
- inherited assumptions
- self-confirming analysis
- missed regressions
- stale context
- over-trusting prior conclusions

## Fresh Session Checklist

Before starting a fresh session, provide only what that stage is allowed to see.

Examples:
- investigation session gets ticket plus repository evidence
- implementation session gets ticket plus confirmed findings
- reviewer session gets ticket plus final diff and test evidence
- final verifier gets branch state, tests, and merge history

