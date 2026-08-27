# Human approval boundary example

## Purpose

Let AI move quickly on reversible internal work while stopping before actions that create external commitments, cost, privacy exposure, or irreversible changes.

## Default rule

> AI may decide and execute inside a defined safe envelope. Crossing the envelope requires explicit human approval.

## Example authority matrix

| Action | AI autonomous? | Why |
|---|---:|---|
| Research public information | Yes | Reversible internal work |
| Compare options and reject weak ideas | Yes | No external commitment |
| Draft an email or proposal | Yes | Draft only |
| Create an internal GitHub Issue | Yes | Auditable and reversible |
| Implement on a branch | Yes | Main remains unchanged |
| Run tests / lint / build | Yes | Deterministic validation |
| Open a PR | Yes | Reviewable, no production commitment |
| Reprioritize internal tasks | Yes | Within existing objective/budget |
| Send an email / proposal | No | External communication |
| Apply to a paid job | No | Creates an external commitment |
| Accept a contract / price | No | Commercial/legal commitment |
| Spend money or enable paid API usage | No | Direct financial impact |
| Send customer/confidential data to an AI service | No | Privacy/security impact |
| Change production data | No | Potentially irreversible impact |
| Force-push / destructive history rewrite | No | Destructive operation |

## Example autonomy budget

```yaml
daily:
  paid_ai_jpy: 0
  external_messages: 0
  new_internal_issues: 5
  experiments: 3
  retry_same_failure: 3

requires_human_approval:
  - external_message
  - job_application
  - contract_or_price_acceptance
  - paid_purchase
  - customer_or_confidential_data_transfer
  - destructive_or_production_change
```

## Runtime behavior

When an action is inside the envelope:

1. AI chooses the next useful action.
2. AI executes it.
3. AI records evidence/result.
4. AI updates the next action.

When an action crosses the envelope:

1. AI completes all safe preparation first.
2. AI presents the exact action waiting for approval.
3. AI explains cost/risk/expected benefit briefly.
4. AI stops only at that boundary, rather than blocking earlier reversible work.

## Example

AI finds a matching freelance job.

Autonomous:
- read the job posting
- compare fit and expected profitability
- draft a customized application
- prepare a public sample
- calculate expected fee after platform cost

Human approval required:
- press the final Submit/Apply button

This keeps the human decision small while leaving the full reasoning trail auditable.
