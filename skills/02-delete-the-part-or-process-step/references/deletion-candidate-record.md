# Deletion Candidate Record

Use this format for every material deletion, deferral, collapse, keep, or investigate decision.

## Candidate Shape

```text
Candidate:
- Item:
- Type: feature / field / state / page / route / API / data relationship / permission / approval / handoff / abstraction / dependency / automation / manual step / other
- Current purpose:
- Evidence inspected:
- Validated-goal link:
- What breaks if removed:
- Who notices:
- Reversibility:
- Safer alternative:
- Classification: Delete now / Defer / Collapse / Keep / Investigate
- Reason:
- Confirmation needed:
- Regression check:
```

## Classifications

### Delete now

Use when:

- no validated goal depends on it,
- the only reason is future speculation,
- an existing capability already covers it,
- it creates duplicated responsibility or a second source of truth,
- it adds operational cost before value is proven,
- removal is reversible or low-risk with clear regression checks.

### Defer

Use when:

- the part might matter later but the current validation gate does not need it,
- keeping it would broaden V1,
- the evidence is real but belongs to a later stage,
- the part should be reintroduced only after a named trigger.

Always name the re-entry trigger.

### Collapse

Use when:

- multiple fields, states, pages, steps, approvals, or components represent the same decision,
- a manual checklist can replace workflow machinery for the demo,
- a narrower rule can replace a configurable system,
- one existing component or API can serve the stable version without a premature abstraction.

### Keep

Use only when there is evidence:

- required by the validated goal or validation gate,
- required by safety, compliance, permissions, data integrity, or customer-visible behavior,
- removal is irreversible and the risk is not understood,
- the user explicitly confirmed it as part of the stable version.

### Investigate

Use when:

- the part is suspicious but evidence is incomplete,
- removal may affect hidden users, data, permissions, or integrations,
- current docs and code disagree,
- deleting now would be a guess.

Investigate is not a parking lot. Name the missing evidence and the next check.

## Confirmation Package

When asking the user, group candidates into one clear package:

```text
Recommended deletion package:
- Delete now:
- Defer:
- Collapse:
- Keep:
- Investigate:

Question:
Should I use this as the stable version boundary?

Options:
1. Yes, use this deletion package. - [impact]
2. Keep [specific disputed item]. - [impact]
3. Pause and investigate [specific risk]. - [impact]
```

Do not ask the user to review a long item-by-item checklist unless the deletion is high-risk.
