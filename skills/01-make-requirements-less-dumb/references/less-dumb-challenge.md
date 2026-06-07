# Less Dumb Challenge

Use this reference before writing a requirement as settled. The goal is to surface questionable points that may be unwise for the customer or enterprise, not to clarify wording and not to delete scope.

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
- Less Dumb Challenge asks: "Now that the requirement is clear enough to inspect, is any part of it unreasonable, misframed, internally inconsistent, or architecturally wrong?"

Use confirmation questions to clarify. Use Less Dumb Challenge to critique.

If the challenge exposes a new material fork, ask one structured confirmation question after stating the challenge. Do not turn every challenge into a question.

## When To Run

Run after:

- enough evidence has been inspected,
- the requirement frame has a customer goal, scope, non-goals, evidence, and validation gate,
- material clarification questions have been answered or recorded as open questions.

If the user asks for a quick read before enough evidence exists, state that the challenge is provisional and name the missing evidence.

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

Use this shape:

```text
Less Dumb Challenge:
- Target:
- Questionable point:
- Evidence:
- Why it may be unwise:
- Whole-project impact:
- Deep-design impact:
- Better framing:
- Classification:
- Confirmation needed, if any:
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

- If a requirement document is created or updated, include the material challenge in the final response.
- If the challenge creates a blocking question, show the challenge first, then ask one structured confirmation question.
- If there is no material challenge, say `No material Less Dumb Challenge found.` Do not omit the section.

## Follow-Up Question

If a challenge would change scope, non-goals, or validation, ask one structured confirmation question using `structured-confirmation.md`.
