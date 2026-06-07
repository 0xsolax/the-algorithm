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

## Project

- [Project Overview](./project-overview.md) - project-wide goals, scope, non-goals, and validation gates.

## Features

- [Feature Name](./feature-name.md) - one-sentence purpose.

## Open Requirement Areas

- Area or question that does not yet have a dedicated document.
```

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

Evidence-backed challenges to questionable requirement, product description, workflow, data, architecture, UX, operational, or validation points. Record only material challenges, not generic skepticism. If no material challenge exists, write `No material Less Dumb Challenge found.`

## Validation Gate

What would prove the requirement is understood well enough to demo, build, delete, optimize, accelerate, or automate.

## Change Log

- YYYY-MM-DD: What changed and why.
```

## Update Rules

- Preserve resolved decisions unless current evidence contradicts them.
- When changing a decision, add a `Change Log` entry explaining the new evidence.
- When the user answers a structured confirmation question, record the answer under `Decisions` or `Confirmation History`.
- Record evidence-backed Less Dumb Challenges when they change framing, open questions, non-goals, or validation gates.
- Keep `Open Questions` for unresolved clarification forks. Keep `Less Dumb Challenge` for unreasonable, risky, inconsistent, or misframed points discovered after inspecting the clarified requirement.
- Do not treat a requirement document as settled if `## Less Dumb Challenge` is missing.
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
- Less Dumb Challenge:
- Remaining blocking question:
- Next validation gate:
```
