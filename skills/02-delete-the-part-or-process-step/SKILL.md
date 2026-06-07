---
name: 02-delete-the-part-or-process-step
description: Remove unjustified parts before optimizing. Use after a requirement, demo, workflow, code path, process, UI, or plan has a clear goal and needs scope reduction, simplification, deletion triage, or removal of steps, features, fields, approvals, abstractions, integrations, or manual handoffs that do not directly serve the validated need.
---

# Delete the Part or Process Step

## Stage Objective

Make the system simpler and more stable by deleting what should not exist. The goal is not elegance; the goal is to remove unjustified parts before anyone spends time optimizing them.

## Core Rule

If the purpose is not clear, the part is suspect. If removing it does not break the validated goal, delete it or defer it.

## Question Budget

- Ask 0-2 questions by default.
- Ask only about protected constraints, ownership, data loss, compliance, or user-visible behavior.
- Do not ask for opinions about every part. Infer from usage, dependencies, docs, tests, and workflow evidence.

## Procedure

1. **Confirm the validated goal**
   - Restate the requirement or demo gate from the prior stage.
   - If there is no validated goal, return to `make-requirements-less-dumb`.

2. **Inventory parts and process steps**
   - List features, UI elements, fields, states, approvals, handoffs, code paths, dependencies, abstractions, and automations involved.
   - Mark which parts are required for the validated goal and which are merely inherited, speculative, or convenient.

3. **Run the deletion test**
   - What breaks if this is removed?
   - Who notices?
   - Is the break tied to the validated goal or to an assumed future?
   - Can the part be replaced by a simpler manual step, existing capability, or narrower rule?
   - Does the part have a responsible owner or hard evidence, not just "the team" or "the process"?

4. **Prefer deletion over improvement**
   - Delete, defer, or collapse before refactoring or redesigning.
   - Do not preserve a part just because it took effort to create.
   - Do not automate a part that should be deleted.
   - If nothing ever needs to be added back, the deletion pass may be too timid.

5. **Define the stable version**
   - State the smallest surviving workflow or implementation.
   - State what is intentionally not present.
   - Define regression checks that prove deletion did not damage the real goal.

## References

- Read `references/deletion-rubric.md` when the deletion decision is ambiguous, politically sensitive, user-visible, or likely to be rationalized as "maybe later".

## Output

Use this compact structure:

```text
Deletion pass:
- Validated goal:
- Required parts:
- Suspect parts:
- Delete now:
- Defer:
- Keep with reason:
- Stable version:
- Regression checks:
- Blocking questions, if any:
```

## Stop Conditions

- If deletion could cause data loss, security exposure, compliance failure, or irreversible customer impact, stop and ask.
- If every part is being kept for "maybe later", challenge the plan and return a smaller stable version.
- If deletion exposes that the original requirement was wrong, return to `make-requirements-less-dumb`.
