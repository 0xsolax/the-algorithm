# Requirements Document

Use this reference before creating, selecting, or updating files under `docs/requirements/`.

The goal is durable customer understanding. A requirement should become clearer across repeated conversations instead of being regenerated from scratch.

## Location

Use this structure:

```text
docs/
  requirements/
    requirements-map.md
    project-overview.md
    <feature-or-domain>.md
```

- `requirements-map.md`: navigation file for all requirements documents.
- `project-overview.md`: project-wide customer goals, scope, and product boundaries.
- `<feature-or-domain>.md`: one feature, workflow, domain, or bounded capability.

Do not create duplicate requirement docs for the same feature. Update the existing document.

## Selection Rule

1. If the customer is asking about the whole project, use `project-overview.md`.
2. If the customer is asking about a feature, workflow, page, API, integration, or domain, use a focused `<feature-or-domain>.md`.
3. If multiple feature docs may apply, read `requirements-map.md` and the likely docs, then ask one targeted question if the boundary is still unclear.
4. If no document exists, create it lazily only after there is a real requirement to preserve.

## requirements-map.md Template

```md
# Requirements Map

This directory records the current understanding of customer requirements. Update existing documents as the understanding changes.

## Algorithm Stage Status

Current recommended skill: `01-make-requirements-less-dumb`
Last updated: YYYY-MM-DD
Status note: Later stages may reopen earlier stages if new evidence changes the requirement, stable version, optimization target, acceleration baseline, or automation gate.

| Stage | Gate | Status | Evidence / Decision | Next Action |
| --- | --- | --- | --- | --- |
| 01 | Requirement Clarification | Not Started |  | Clarify the real requirement and update the relevant requirement doc. |
| 01 | Less Dumb Challenge Dialogue | Not Started |  | Run after requirement clarification is marked `Clarified`. |
| 02 | Deletion Pass | Not Started |  | Propose deletion, deferral, or collapse after 01 is resolved. |
| 02 | Stable Version Boundary | Not Started |  | Confirm the smaller stable version before optimization. |
| 03 | Optimization Pass | Not Started |  | Optimize only the confirmed stable version. |
| 04 | Acceleration Pass | Not Started |  | Measure and accelerate only after optimization is stable. |
| 05 | Automation Gate | Not Started |  | Automate only after the workflow is stable, validated, optimized, and measurable. |

## Project

- [Project Overview](./project-overview.md) - project-wide goals, scope, non-goals, and validation gates.

## Features

- [Feature Name](./feature-name.md) - one-sentence purpose.

## Open Requirement Areas

- Area or question that does not yet have a dedicated document.
```

## Algorithm Stage Status Rules

- Keep `Algorithm Stage Status` in `requirements-map.md`; do not create a separate status file.
- `01-make-requirements-less-dumb` initializes the table when it is missing.
- Every Algorithm skill must read the table before starting and update its own row before stopping.
- Later stages may reopen earlier rows when new evidence invalidates an assumption; record the reason in `Evidence / Decision`.
- Status can also be corrected forward when current evidence proves a gate has already passed; record the evidence instead of preserving stale status.
- Keep `Current recommended skill` aligned with the earliest unresolved gate.
- Use these status vocabularies:
  - `Requirement Clarification`: `Not Started`, `In Progress`, `Clarified`, `Reopened`, `Blocked`.
  - `Less Dumb Challenge Dialogue`: `Not Started`, `In Progress`, `Resolved`, `Reopened`, `Blocked`.
  - `Deletion Pass`: `Not Started`, `In Progress`, `Proposed`, `Confirmed`, `Reopened`, `Blocked`.
  - `Stable Version Boundary`: `Not Started`, `In Progress`, `Confirmed`, `Reopened`, `Blocked`.
  - `Optimization Pass`: `Not Started`, `In Progress`, `Confirmed`, `Reopened`, `Blocked`.
  - `Acceleration Pass`: `Not Started`, `Measured`, `In Progress`, `Confirmed`, `Blocked`.
  - `Automation Gate`: `Not Started`, `Ready`, `In Progress`, `Confirmed`, `Not Appropriate`, `Blocked`.
- Recommended skill routing:
  - If `Requirement Clarification` is not `Clarified`, use `01-make-requirements-less-dumb`.
  - If `Requirement Clarification` is `Clarified` and `Less Dumb Challenge Dialogue` is not `Resolved`, keep using `01-make-requirements-less-dumb`.
  - If 01 is resolved and `Stable Version Boundary` is not `Confirmed`, use `02-delete-the-part-or-process-step`.
  - If the stable version is confirmed and `Optimization Pass` is not `Confirmed`, use `03-optimize`.
  - If optimization is confirmed and `Acceleration Pass` is not `Confirmed`, use `04-accelerate`.
  - If acceleration is confirmed, or deliberately not needed with evidence, use `05-automate` to decide whether automation is appropriate.

## Requirement Document Template

Write requirement documents in English.

```md
# Requirements: {Project or Feature Name}

## Current Understanding

Plain-English summary of what the customer appears to want now.

## Customer Goal

The real outcome the customer is trying to achieve.

## Scope

What is included.

## Non-Goals

What is explicitly not included.

## Evidence

- Conversation:
- Project docs:
- Code or workflow paths:
- Screenshots, issues, examples, or artifacts:

## Open Questions

Questions that would materially change scope, direction, or validation.

## Decisions

Resolved requirement decisions with short context.

## Confirmation History

Short record of user-confirmed answers that changed the requirement.

## Less Dumb Challenge

Evidence-backed challenges to questionable requirement, product description, workflow, data, architecture, UX, operational, or validation points. This section records the outcome of the Less Dumb Challenge Dialogue after the user has had a chance to respond; it is not a substitute for the dialogue. The chat dialogue should be plain-language discussion, while this document may record the outcome in structured notes. If no material challenge exists, write `No material Less Dumb Challenge found.`

## Validation Gate

What would prove the requirement is understood well enough to demo, build, delete, optimize, accelerate, or automate.

## Change Log

- YYYY-MM-DD: What changed and why.
```

## Update Rules

- Preserve resolved decisions unless current evidence contradicts them.
- When changing a decision, add a `Change Log` entry explaining the new evidence.
- When the user answers a structured confirmation question, record the answer under `Decisions` or `Confirmation History`.
- When material clarification is complete, mark `Requirement Clarification` as `Clarified` in `requirements-map.md`.
- When docs, plans, design, implementation, tests, demos, or user acceptance show clarification has already happened, mark `Requirement Clarification` as `Clarified` with an evidence note instead of asking redundant clarification questions.
- Record evidence-backed Less Dumb Challenges when they change framing, open questions, non-goals, or validation gates.
- Keep `Open Questions` for unresolved clarification forks. Keep `Less Dumb Challenge` for unreasonable, risky, inconsistent, or misframed points discovered after inspecting the clarified requirement.
- Do not treat a requirement document as settled if `## Less Dumb Challenge` is missing.
- Do not mark `Less Dumb Challenge Dialogue` as `Resolved` until the user has responded to material challenges, or there is no material challenge to discuss.
- If a Less Dumb Challenge turns into a broad positioning, scope, user, or validation question, mark `Requirement Clarification` as `Reopened`; do not keep asking clarification questions inside the challenge stage.
- Keep implementation details out unless they are direct evidence for the requirement.
- Keep questions only if the answer would change scope, direction, or validation.
- Prefer tightening existing text over appending duplicate summaries.
- If the document is becoming too broad, split a feature doc and update `requirements-map.md`.

## Chat Output After Updating

After updating a requirement doc, report:

```text
Requirement doc:
- Created/updated:
- Key change:
- Confirmed:
- Algorithm Stage Status:
- Less Dumb Challenge:
- Remaining blocking question:
- Next validation gate:
```
