# Stage Inference

Use this reference after the Evidence Floor and before asking requirement clarification questions.

The goal is to infer where the work actually is in the Algorithm, then correct `Algorithm Stage Status` when evidence shows the current status is stale.

## Core Rule

Do not ask early-stage requirement questions when the project evidence shows the requirement has already been clarified, planned, designed, or implemented.

If the work is already past clarification, update `requirements-map.md` and move to the earliest unresolved gate.

## Evidence To Inspect

Look for current evidence, not memory:

- `docs/requirements/requirements-map.md`
- relevant requirement docs under `docs/requirements/`
- plan and design docs such as `pdoc/plan`, `pdoc/design`, `PLAN_*.md`, `DESIGN_*.md`
- implemented routes, pages, APIs, schemas, tests, fixtures, demos, screenshots, or preview artifacts
- recent diffs, test results, browser verification, release notes, or user acceptance notes
- conversation decisions from the current thread

## Stage Signals

### Requirement clarification is probably not complete

Signals:

- no relevant requirement doc exists,
- goal, user, scope, non-goals, or validation gate are missing,
- the user is still deciding basic positioning or first successful user,
- implementation evidence is absent or unrelated,
- challenge would depend on unresolved V1 positioning, scope, user, or validation.

Action:

- keep or set `Requirement Clarification` to `In Progress` or `Reopened`,
- continue structured confirmation,
- do not start Less Dumb Challenge Dialogue yet.

### Requirement clarification is probably complete

Signals:

- requirement doc has customer goal, scope, non-goals, decisions, evidence, and validation gate,
- user has answered the material requirement forks,
- plan or design doc already uses a stable requirement framing,
- implementation or demo aligns with a clear requirement,
- asking a basic requirement question would duplicate decisions already recorded in docs or implementation.

Action:

- mark `Requirement Clarification` as `Clarified`,
- record evidence in `Evidence / Decision`,
- if `Less Dumb Challenge Dialogue` is not `Resolved`, set `Current recommended skill` to `01-make-requirements-less-dumb` and start that dialogue.

### Demo or implementation already exists

Signals:

- routes, pages, components, APIs, migrations, tests, or browser-verification artifacts exist for the requirement,
- a plan or design has already been implemented,
- user is reacting to a working demo rather than proposing an initial idea.

Action:

- do not ask "what should V1 be?" unless docs and implementation contradict each other,
- treat requirement clarification as already passed when evidence is coherent,
- move directly to `Less Dumb Challenge Dialogue` if unresolved,
- if the challenge finds that the implementation proves a different requirement than the docs, mark `Requirement Clarification` as `Reopened`.

### Less Dumb Challenge Dialogue is the current gate

Signals:

- requirement clarification is already `Clarified`,
- the feature has docs, design, or implementation,
- material challenge concerns are about whether the clarified requirement is wise, not about what the user meant.

Action:

- mark `Less Dumb Challenge Dialogue` as `In Progress`,
- discuss one challenge naturally,
- do not ask broad clarification questions unless you reopen clarification.

### 01 is probably complete

Signals:

- `Requirement Clarification` is `Clarified`,
- `Less Dumb Challenge Dialogue` is `Resolved`,
- requirement doc records challenge outcomes or `No material Less Dumb Challenge found.`,
- validation gate is clear enough for deletion or stable-version review.

Action:

- set `Current recommended skill` to `02-delete-the-part-or-process-step`,
- do not continue 01 unless new evidence reopens clarification or challenge.

## Status Correction Rules

- Status can be corrected from evidence. Do not preserve stale `Not Started` or `In Progress` if implementation, docs, and conversation prove the gate is already passed.
- When correcting a status, write a short evidence note such as: `Inferred clarified from requirement doc, design doc, implemented demo, and user acceptance on YYYY-MM-DD.`
- Do not mark `Less Dumb Challenge Dialogue` as `Resolved` merely because the demo exists. It is resolved only after the user responds to material challenges or there is no material challenge.
- Do not mark a later stage complete from vibes. Use concrete docs, code, tests, demos, or user decisions.
- If evidence conflicts, mark the earliest conflicting gate as `Reopened` and explain why.

## Output Shape

Use this compact shape when stage inference matters:

```text
Stage inference:
- Current evidence:
- Existing status:
- Inferred maturity:
- Status correction:
- Current recommended skill:
- Why not asking requirement clarification:
- Earliest unresolved gate:
```
