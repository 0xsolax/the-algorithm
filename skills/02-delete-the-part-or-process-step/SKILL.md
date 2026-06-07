---
name: 02-delete-the-part-or-process-step
description: Produce evidence-backed deletion, deferral, and collapse proposals after a requirement, demo gate, workflow, code path, process, UI, or plan has a clear validated goal. Use to deep-dive the relevant project surface, compare it against docs/requirements and prior Less Dumb Challenges, identify unjustified features, fields, states, pages, APIs, approvals, abstractions, dependencies, automations, or manual handoffs, and ask the user to confirm a smaller stable version before optimizing.
---

# Delete the Part or Process Step

## Stage Objective

Turn a clarified requirement into a smaller stable version by finding what can be deleted, deferred, or collapsed before anyone optimizes it.

This skill is a deletion proposal workflow, not an automatic deletion executor. It should boldly surface parts that do not serve the validated goal, but only after a deep evidence pass.

## Core Rules

- Do not delete to appear rigorous. Delete only after evidence shows the part does not serve the validated goal.
- If there is no validated goal, requirement doc, demo gate, or decision frame, return to `01-make-requirements-less-dumb`.
- Use current project evidence over memory, taste, or generic minimalism.
- Read requirement records before judging: `docs/requirements/requirements-map.md`, `Algorithm Stage Status`, the relevant feature or project requirement, and any `Less Dumb Challenge` section.
- Do not start a normal deletion pass until `Requirement Clarification` is `Clarified` and `Less Dumb Challenge Dialogue` is `Resolved`; otherwise return to `01-make-requirements-less-dumb` or state that the deletion pass is provisional.
- Separate proposals from execution. Ask the user to confirm deletion, deferral, or collapse before making irreversible, user-visible, data, permission, or architecture changes.
- Prefer a smaller stable version over a "complete" V1 that cannot be validated cleanly.

## Question Budget

- Ask 0-2 questions by default.
- Ask one grouped deletion confirmation instead of interrogating every candidate.
- Ask only about protected constraints: data loss, compliance, permissions, customer-visible behavior, ownership, irreversible migration, or a deletion package that changes the stable version.
- If evidence is enough, present the recommended deletion package and ask for confirmation.

## Procedure

1. **Confirm the validated goal**
   - Read `Algorithm Stage Status` in `docs/requirements/requirements-map.md`.
   - Read the relevant requirement document and validation gate.
   - Pull forward confirmed scope, non-goals, decisions, open questions, and prior Less Dumb Challenges.
   - If the requirement is still unclear, stop and return to `01-make-requirements-less-dumb`.
   - Mark `Deletion Pass` as `In Progress` when the deletion pass starts.

2. **Inventory the relevant surface**
   - List the features, UI elements, fields, states, pages, routes, APIs, data relationships, permissions, approvals, handoffs, code paths, components, dependencies, abstractions, scripts, automations, and manual steps involved.
   - Mark which items are directly required by the validated goal and which are inherited, speculative, duplicated, future-facing, or convenience-driven.

3. **Deep dive before proposing deletion**
   - Inspect docs, plans, code, callers, workflows, examples, screenshots, tests, and current behavior for the suspicious items.
   - For each suspect item, answer: what breaks if removed, who notices, whether the break affects the validation gate, and whether a simpler existing capability can replace it.
   - Do not propose deletion from naming, vibes, or "minimalism" alone.

4. **Run deletion lenses**
   - Read `references/deletion-lenses.md`.
   - Use both the Whole-Project Lens and Deep-Design Lens.
   - Look for parts that create duplicated sources of truth, premature stage work, unnecessary operational cost, wrong domain coupling, redundant states, copied UI shape, or validation noise.

5. **Classify deletion candidates**
   - Read `references/deletion-candidate-record.md`.
   - Classify each material candidate as `Delete now`, `Defer`, `Collapse`, `Keep`, or `Investigate`.
   - Keep only with evidence. "Maybe later", "looks complete", or "already built" is not enough.

6. **Define the stable version**
   - Read `references/stable-version.md`.
   - State the smallest surviving workflow, product surface, or implementation that still satisfies the validation gate.
   - State what is intentionally absent and why.
   - Define regression checks that prove deletion did not damage the real goal.

7. **Ask for deletion confirmation**
   - Present one deletion package or one highest-impact deletion fork.
   - Mark `Deletion Pass` as `Proposed` when asking for confirmation.
   - Include the recommended option first and explain the impact.
   - If the user confirms the stable version boundary, mark `Deletion Pass` as `Confirmed`, mark `Stable Version Boundary` as `Confirmed`, and set `Current recommended skill` to `03-optimize`.
   - If the user confirms and explicitly asks for implementation, proceed with scoped edits. Otherwise preserve the proposal as a plan or requirement update.

## References

- Read `references/deletion-lenses.md` before deciding what should be deleted, deferred, or collapsed.
- Read `references/deletion-candidate-record.md` when recording material candidates or asking the user to confirm a deletion package.
- Read `references/stable-version.md` before claiming the remaining version is stable.
- Read `references/deletion-rubric.md` when a candidate is ambiguous, politically sensitive, user-visible, or likely to be rationalized as "maybe later".

## Output

Use this compact structure:

```text
Deletion pass:
- Validated goal:
- Requirement docs inspected:
- Algorithm Stage Status:
- Prior Less Dumb Challenge used:
- Surfaces inspected:
- Stable version:
- Required parts:
- Delete now:
- Defer:
- Collapse:
- Keep with evidence:
- Investigate:
- Recommended deletion package:
- User confirmation needed:
- Regression checks:
- Requirement or plan updates:
```

## Stop Conditions

- If the validated goal is missing or contradicted by evidence, return to `01-make-requirements-less-dumb`.
- If `Algorithm Stage Status` is missing from `requirements-map.md`, return to `01-make-requirements-less-dumb` to initialize it.
- If `Less Dumb Challenge Dialogue` is not `Resolved`, return to `01-make-requirements-less-dumb` before a normal deletion pass.
- If deletion could cause data loss, security exposure, compliance failure, permission leakage, irreversible migration, or serious customer impact, stop and ask.
- If every part is kept for "maybe later", challenge the plan and produce a smaller stable version.
- If no evidence-backed deletion exists, say so and list what evidence would change that conclusion.
- If deletion exposes that the original requirement is wrong, return to `01-make-requirements-less-dumb`.
