# Deletion Rubric

Use this reference when a candidate is ambiguous, politically sensitive, user-visible, or likely to be rationalized as "maybe later".

## Deletion Test

For each candidate, answer:

- What validated goal does this serve?
- What evidence proves that link?
- What breaks if it is removed?
- Who notices the break?
- Does the break affect the validation gate or only a future assumption?
- Is there a simpler existing capability, manual step, or narrower rule?
- Is the part reversible?
- Does it involve data loss, permissions, compliance, reporting, or committed customer behavior?

If these answers are unknown, classify as `Investigate`, not `Delete now`.

## Delete Now

Delete when:

- no validated goal depends on it,
- the only reason is "maybe later",
- it exists because of inherited process, not current need,
- it hides unclear ownership or duplicated responsibility,
- it creates a second source of truth,
- it can be replaced by an existing capability or a simpler manual step,
- it adds operational cost before value is proven.

## Defer

Defer when:

- it might matter later but has no evidence now,
- keeping it increases complexity in the stable version,
- the next demo or decision gate does not need it,
- the part belongs to optimization, acceleration, or automation rather than current validation.

Name the re-entry trigger. "Later" is not a trigger.

## Collapse

Collapse when:

- multiple steps exist only to transfer information,
- two states, fields, pages, prompts, or approvals represent the same decision,
- a manual checklist can replace workflow machinery for the demo,
- fixed behavior can replace configuration for the stable version,
- one narrow component can replace a premature shared abstraction.

## Keep

Keep only when there is evidence:

- required by the validated goal,
- required by safety, compliance, permissions, data integrity, reporting, or user-visible behavior,
- required because removal is irreversible and the risk is not understood,
- explicitly confirmed by the user as part of the stable version.

## Investigate

Investigate when:

- docs and code disagree,
- the owner or user is unclear,
- removal may affect hidden workflows,
- the part touches data migrations, permissions, compliance, or external integrations,
- the evidence is too thin to classify honestly.

Name the next evidence check.

## Red Flags

- Every item is kept.
- No add-back risk is accepted.
- Every deletion is low-impact polish rather than real scope reduction.
- The answer says "simple enough" but cannot name the purpose.
- A part is kept because it was expensive to build.
- A part is deleted because it looks ugly, old, or boring without evidence.
- The deletion pass starts optimizing code before deleting scope.
