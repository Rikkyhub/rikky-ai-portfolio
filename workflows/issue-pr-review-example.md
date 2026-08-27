# AI-assisted Issue → PR → Review workflow

## Purpose

Turn one concrete request into a reviewable change while keeping the work auditable and preventing an AI agent from silently expanding scope.

## Example request

> Update a form so required fields appear before optional fields on mobile. Do not change desktop behavior or analytics event names.

## Workflow

### 1. Convert the request into an execution contract

Before editing code, record:

- **Goal** — what user-visible outcome should change
- **Scope** — files/components likely involved
- **Non-goals** — what must not change
- **Acceptance criteria** — observable checks that prove completion
- **Risk boundaries** — destructive, external, production, credential or privacy-sensitive actions

Example:

```text
Goal: Required fields appear before optional fields on mobile.
Non-goals: Desktop order unchanged. Analytics event names unchanged.
Acceptance: 390px view verified, desktop regression check passes, existing analytics tests pass.
```

### 2. Inspect before modifying

AI should first inspect the relevant implementation, tests and project rules.

Do not create a replacement architecture when a small local change satisfies the request.

### 3. Implement the smallest coherent change

- use a branch, never direct `main`
- keep unrelated formatting/refactors out of the diff
- preserve existing behavior outside the explicit scope
- add or update tests only where they protect the requested behavior

### 4. Validate deterministically first

Prefer deterministic checks before semantic AI review:

1. targeted unit/integration tests
2. typecheck/lint when relevant
3. build when relevant
4. visual check when UI changed

Never report a check as PASS unless it actually ran successfully.

### 5. Open a PR with evidence

PR should answer:

- What changed?
- Why was this the smallest correct change?
- What was tested?
- What remains uncertain?
- Is any human decision needed?

### 6. Review against the original contract

The reviewer should compare the diff with the original goal/non-goals, not only ask whether the code looks valid.

Typical review questions:

- Did the change solve the exact requested problem?
- Did scope expand?
- Are existing behaviors unintentionally changed?
- Is evidence sufficient?
- Are any statements in the PR unsupported?

### 7. Fix or merge

If a blocking problem exists, leave a concrete correction on the PR and fix it on the same branch.

If the change is safe, scoped and validated, merge it. Non-blocking questions can remain documented without stopping unrelated safe work.

## Stop conditions

AI must stop and request a human decision when the next step requires:

- credentials or secret access not already authorized
- production/destructive changes outside standing permission
- sending an external message or application
- spending money
- handling confidential/customer data without an approved boundary
- materially expanding the requested scope

## Why this pattern

The goal is not maximum agent activity. The goal is to let AI do most reversible internal work while keeping decisions, evidence and risk boundaries visible in GitHub.
