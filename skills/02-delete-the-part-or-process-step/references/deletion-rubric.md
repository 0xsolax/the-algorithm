# Deletion Rubric

Use this reference when deciding whether to delete, defer, collapse, or keep a part or process step.

## Classify Each Part

```text
Part:
- Purpose:
- Evidence it serves the validated goal:
- Owner:
- What breaks if removed:
- Who notices:
- Delete / defer / collapse / keep:
- Regression check:
```

## Delete

Delete when:

- No validated goal depends on it.
- The only reason is "maybe later".
- It exists because of inherited process, not current need.
- It hides unclear ownership or duplicated responsibility.
- It can be replaced by an existing capability or a simpler manual step.

## Defer

Defer when:

- It might matter later but has no evidence now.
- Keeping it increases complexity in the stable version.
- The next demo or decision gate does not need it.

## Collapse

Collapse when:

- Multiple steps exist only to transfer information.
- Two states, fields, pages, prompts, or approvals represent the same decision.
- A manual checklist can replace workflow machinery for the demo.

## Keep

Keep only when there is evidence:

- Required by the validated goal.
- Required by safety, compliance, permissions, data integrity, or user-visible behavior.
- Required because removal is irreversible and the risk is not yet understood.

## Red Flags

- Every item is kept.
- No add-back risk is accepted.
- The answer says "simple enough" but cannot name the purpose.
- A part is kept because it was expensive to build.
