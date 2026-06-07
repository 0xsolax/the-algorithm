# Structured Confirmation

Use this reference before asking the user to confirm scope, goal, non-goals, validation gates, or unresolved requirement forks.

The goal is not to interview endlessly. The goal is to surface the few uncertainties that would change the requirements document.

## Hard Rules

- Ask exactly one question per round.
- Provide the recommended answer for every question.
- Provide 2-3 concrete options for every question.
- Stop after asking; wait for the user's answer before continuing.
- If repo or document evidence can answer the question, inspect evidence instead of asking.
- After the user answers, update the requirement frame and requirement document before asking the next question.
- Do not ask open-ended prompts like "what do you think?" unless included as a free-form escape after concrete options.

## Before Asking

Build a requirement frame first:

```text
Requirement frame:
- Customer goal:
- Proposed scope:
- Non-goals:
- Evidence:
- Decisions that seem settled:
- Uncertainties that would change the document:
- Recommended next assumption:
```

Do not ask questions that project evidence can answer. Inspect the repo, docs, issues, screenshots, or code path first.

## Five-Round Limit

Use at most 5 confirmation rounds for the basic requirement shape.

Each round should remove one major uncertainty:

1. Real customer goal.
2. Scope boundary.
3. Non-goal or deletion candidate.
4. Validation gate.
5. Risk, constraint, or unresolved tradeoff.

Stop earlier when the requirement is clear enough to update the document and define a demo gate.

## Native Choice Prompt

When the environment provides a native structured question or choice prompt, prefer it:

- Ask one short question.
- Offer 2-3 mutually exclusive choices.
- Put the recommended choice first.
- Explain the impact of each choice in one sentence.
- Allow a free-form escape when the environment supports it.

If no native prompt is available, write the same structure in chat. Do not mention mode switching unless the user explicitly asks why no native dialog appeared.

## Question Shape

Every question must be tied to evidence and a decision. Use this exact shape:

```text
Evidence:
[one sentence about what was inspected]

Why this matters:
[one sentence about what changes in scope, non-goals, demo, or validation]

Question:
[one short question]

Recommended:
[choice A] - [one sentence reason]

Options:
1. [choice A] - [impact]
2. [choice B] - [impact]
3. [choice C] - [impact]
```

Bad question:

```text
What features do you want?
```

Good question:

```text
Evidence:
I found both admin-facing setup notes and user-facing onboarding copy.

Why this matters:
This changes whether the first demo should prove internal configuration or end-user activation.

Question:
Who is the first successful user?

Recommended:
Internal operator - the current repo has setup docs but no user activation flow.

Options:
1. Internal operator - demo setup and review workflow first.
2. End user - demo activation and self-service first.
3. Both - split requirements into two feature docs.
```

## After Each Answer

Immediately update the requirement frame:

- Move confirmed items to `Decisions`.
- Keep unresolved items in `Open Questions`.
- Update `Scope`, `Non-Goals`, and `Validation Gate`.
- Decide whether another question is still worth one of the 5 rounds.

Do not wait until the end of the conversation to preserve the decision.

## Drift Guard

If the agent starts giving a general opinion instead of the fixed question shape, reset:

```text
I need to tighten this into one confirmation question.
```

Then emit exactly one question using the required shape.
