# Less Dumb Challenge

Use this reference after requirement clarification is complete. The goal is to run a user-facing, plain-language dialogue about questionable points that may be unwise for the customer or enterprise, not to clarify wording, not to delete scope, and not to write a report without user response.

## Purpose

Challenge the clarified requirement from whole-project and deep-design perspectives:

- Does it fit the project boundary?
- Does it solve the right business problem?
- Does it duplicate an existing workflow or capability?
- Does it create operational cost before value is proven?
- Does it ask for automation, configurability, or complexity too early?
- Does it make validation harder than necessary?

## Separation From Confirmation

Do not mix Less Dumb Challenge with structured confirmation.

- Structured confirmation asks: "What does the user mean, and which fork should the requirement document record?"
- Less Dumb Challenge Dialogue asks: "Now that the requirement is clear enough to inspect, is any part of it unreasonable, misframed, internally inconsistent, or architecturally wrong?"

Use confirmation questions to clarify. Use Less Dumb Challenge Dialogue to critique and decide what to do about the critique.

If the challenge exposes a new material fork, ask one structured confirmation question after stating the challenge. Do not turn every challenge into a report-only section.

If the challenge depends on an unresolved V1 positioning, user, scope, or validation fork, the requirement was not actually clarified. Mark `Requirement Clarification` as `Reopened` and return to structured confirmation. Do not smuggle requirement clarification into the challenge stage.

If docs, plans, design, implementation, tests, or a demo already show the V1 positioning, treat that positioning as the starting point for critique. Do not ask the user to re-decide the positioning unless the evidence conflicts.

## When To Run

Run after:

- enough evidence has been inspected,
- the requirement frame has a customer goal, scope, non-goals, evidence, and validation gate,
- material clarification questions have been answered or recorded as open questions.
- `Requirement Clarification` is marked `Clarified` in `docs/requirements/requirements-map.md`.

If the user asks for a quick read before enough evidence exists, state that the challenge is provisional and name the missing evidence.

## Dialogue Rule

Less Dumb Challenge is a dialogue gate.

- Before starting, mark `Less Dumb Challenge Dialogue` as `In Progress` in `requirements-map.md`.
- Present at most one material challenge at a time.
- Speak like a senior product or engineering partner, not like a table.
- Give a clear point of view first: "I am worried about X because Y. I would handle it by Z."
- Invite pushback or confirmation conversationally; do not default to 2-3 options.
- Use structured options only when the user must choose between concrete requirement changes.
- After the user answers, update the requirement document and the status table.
- Mark `Less Dumb Challenge Dialogue` as `Resolved` only after all material challenges are resolved or no material challenge exists.
- If a challenge changes the real requirement, mark `Requirement Clarification` as `Reopened` and record why.

## Human Language Rule

Think with structure; speak naturally.

Do not write the user-facing challenge as:

```text
Target:
Questionable point:
Evidence:
Why it matters:
Options:
```

That reads like a report or another requirements questionnaire.

Instead, write a short discussion:

```text
I think one part is worth pushing on before we call this stable.

The current design keeps row actions conservative: users often land on a filtered source list rather than a specific source record. That is probably the right V1 tradeoff if we are proving supplier context first, because it avoids promising the workspace is already an operations console. But it also means the demo must be framed honestly. If users expect to handle a purchase order directly from this page, this will feel one step short.

My recommendation is not to upgrade it now. I would record this as a V1 validation risk: demo it as a supplier context workspace, watch whether users complain about not landing on the exact record, and only then decide whether V2 should become more operational.
```

The challenge can end with a soft invitation:

```text
If you see this page as an operations console rather than a context workspace, that would reopen the requirement. Otherwise I would keep the current implementation and validate this risk in the demo.
```

Do not ask broad positioning questions like "Is this an overview or operation page?" during the challenge. That question belongs to requirement clarification. In the challenge stage, make an evidence-backed argument from the already clarified position.

## Challenge Lenses

Use both lens groups.

### Whole-Project Lens

Look for problems at the product or enterprise level:

- Project boundary: this may belong to another module, phase, or product.
- Business value: this may not solve the real customer or operator problem.
- Workflow duplication: this may recreate an existing process, page, approval path, or report.
- Capability overlap: this may add a second source of truth.
- Operational cost: this may require maintenance, permissions, training, cleanup, or governance before value is proven.
- Rollout and validation: this may be too broad to demo or validate cleanly.
- Stage mismatch: this may optimize, accelerate, or automate before the requirement is stable.

### Deep-Design Lens

Look for problems inside the requirement or design:

- Requirement wording hides an assumption, overloaded term, or wrong object name.
- Product description copies another page's shape while the domain model is different.
- Data model, identity, ownership, status, or lifecycle semantics do not match the proposed UI.
- Architecture would couple unrelated domains, permissions, adapters, or storage models.
- UX label or navigation wording could mislead users into the wrong workflow.
- Edge cases would become core complexity rather than validation detail.
- Validation gate proves implementation effort but not customer value.
- The first demo requires backend, frontend, data migration, permissions, and workflow changes when a thinner proof would work.

## Evidence Requirement

Every challenge must cite evidence. Acceptable evidence includes:

- Existing requirements docs.
- Project docs, rules, plans, or design notes.
- Code, config, route, API, workflow, or test paths.
- Screenshots, issues, examples, or user-facing docs.
- Conversation facts confirmed by the user.
- Operational or enterprise constraints surfaced in the current project.

If there is no evidence-backed challenge, say:

```text
No material Less Dumb Challenge found.
```

Do not invent objections to appear skeptical.

## Challenge Limit

- Default: 0-2 challenges.
- Maximum: 3 challenges.
- If more than 3 concerns appear, group them by underlying questionable assumption.

## Challenge Shape

Use this as private scratch notes only. Do not paste it verbatim to the user:

```text
Private challenge notes:
- What I am worried about:
- Evidence behind the worry:
- Why this may hurt the project or design:
- The framing I would recommend:
- Whether this reopens clarification:
- How I will say this in plain language:
```

Use the requirement document only to record the outcome after the user responds:

```text
Less Dumb Challenge outcome:
- Challenge:
- User decision:
- Requirement change:
- Status: Resolved / Kept with risk / Reopened clarification / Needs more evidence
```

## What Counts

Good challenges:

- "This proposes a second approval workflow, but the project already has one approval path."
- "This assumes self-service users, but current docs and routes are operator-facing."
- "This adds automation before the manual workflow has a stable validation gate."
- "This asks for broad configurability, but the evidence only supports one current case."
- "This reuses a customer-facing label in a supplier workflow, but the domain evidence points to purchase-side records."
- "This suggests sharing one storage model, but the master-id semantics differ between the two domains."

Weak challenges:

- "This might be overdesigned" without evidence.
- "Maybe users won't need it" without a user or workflow reason.
- "This seems complex" without identifying the cost or simpler framing.

## Stage Boundary

Do not remove scope in this stage.

Instead classify questionable points as:

- `Needs confirmation`
- `Candidate non-goal`
- `Better-framed requirement`
- `Open question`

The actual deletion decision belongs to `02-delete-the-part-or-process-step`.

## Visibility Rule

The challenge must be visible to the user.

- Do not only write challenges into the requirement document.
- If material challenges exist, present them as a dialogue before marking the stage resolved.
- If the challenge creates a blocking question, show the challenge first, then ask one structured confirmation question.
- If there is no material challenge, say `No material Less Dumb Challenge found.`, record that outcome, and mark `Less Dumb Challenge Dialogue` as `Resolved`.

## Follow-Up Question

If a challenge would change scope, non-goals, or validation, ask one structured confirmation question using `structured-confirmation.md`.
