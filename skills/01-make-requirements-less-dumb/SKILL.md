---
name: 01-make-requirements-less-dumb
description: Pressure-test, clarify, and durably document rough product, engineering, workflow, PRD, issue, or feature requests before implementation. Use when a request is vague, overbuilt, assumption-heavy, solution-first, or when Codex needs to create or update docs/requirements so the customer's real need, scope, non-goals, evidence, open questions, and validation gate do not disappear after the conversation.
---

# Make Requirements Less Dumb

## Stage Objective

Turn a rough request into a durable requirements document and a validated working hypothesis. The goal is not to collect every possible requirement; the goal is to identify the real problem, expose questionable assumptions, update the right requirement file, and reduce the next step to a demo or decision gate.

## Core Rule

Read first. Infer next. Ask only if the answer changes the next action.

Do not make the user fill out a long questionnaire. Use the current conversation, repo docs, issues, product notes, screenshots, logs, and prior decisions before asking.

When a real requirement is discovered, preserve it in `docs/requirements/` so future sessions refine the same document instead of starting over.

## Evidence Floor

Before forming a working hypothesis, inspect enough current-state evidence to make the hypothesis falsifiable:

1. Confirm the working path or repo root.
2. Inventory the project surface with a file tree or search.
3. Read source-of-truth docs if present: README, AGENTS/CLAUDE, rules, guides, plans, design docs, issue text, or product notes.
4. If the request touches implementation, inspect relevant config, entrypoints, callers, or code paths.
5. If the request touches product or workflow, inspect existing UX, examples, screenshots, process artifacts, or user-facing docs.

For small repositories, read the whole project surface and key files. For large repositories, first make a map, then read source-of-truth docs and relevant paths. Do not claim a confident project-level judgment from conversation history alone.

## Question Budget

- Ask 0 questions when context supports a reversible next step.
- Ask 1-3 questions when there is a real fork in direction.
- Ask up to 5 confirmation rounds when the basic requirement frame has unresolved material uncertainties that cannot be inferred.
- If you need more than 5 questions, stop and present your current assumptions instead of continuing the interrogation.

Every question must be attached to an evidence-backed decision fork, for example: "The repo has both admin setup docs and user-facing onboarding copy. Which user should the first demo validate?"

When the environment provides a native structured question or choice prompt, use it for confirmation: one short question, 2-3 mutually exclusive answers, recommended option first, and a free-form escape when available. If no native prompt is available, ask the same question in chat.

Hard rule: confirmation questions must not become loose discussion prompts. Ask one question, provide a recommended answer, provide 2-3 concrete options, wait for the user's answer, then update the requirement frame before asking anything else.

Hard rule: structured confirmation and Less Dumb Challenge are separate gates. Structured confirmation clarifies what the user wants and preserves it in requirements. Less Dumb Challenge critiques whether the clarified requirement, description, workflow, data shape, or architecture is unreasonable, harmful, overbuilt, inconsistent, or solving the wrong problem.

Hard rule: the Less Dumb Challenge must be visible work. Do not bury it only in the requirement document. If a final answer updates requirements, include either the material Less Dumb Challenge or `No material Less Dumb Challenge found.`

## Procedure

1. **Collect context**
   - Satisfy the Evidence Floor before judging.
   - Read local project guidance, current plans, issues, comments, screenshots, logs, or existing code paths that are directly relevant.
   - Prefer current source-of-truth files over memory or generic best practices.

2. **Find or create the requirements document**
   - Use `docs/requirements/requirements-map.md` as the navigation file.
   - Use `docs/requirements/project-overview.md` for project-wide requirements.
   - Use `docs/requirements/<feature-or-domain>.md` for feature, workflow, or domain-specific requirements.
   - If the right document exists, update it instead of creating a duplicate.
   - Create files lazily only when there is a requirement worth recording.
   - Write requirements documents in English, even when chatting with the user in another language.

3. **Zoom out before judging**
   - If the area is unfamiliar, produce a short map first: domain objects, relevant modules or files, callers or workflow steps, source-of-truth documents, and unknown surfaces.
   - Use project vocabulary rather than generic labels.
   - If no project files or artifacts are available, say so and downgrade confidence.

4. **Form a falsifiable working hypothesis**
   - State what the user probably wants.
   - State what the request is probably not asking for.
   - Name the most suspicious part of the proposed requirement.
   - Include the evidence sentence: "I believe the real requirement is X because evidence A/B/C."
   - State what evidence would disprove or change the hypothesis.

5. **Build the requirement frame**
   - Draft the customer goal, scope, non-goals, evidence, open questions, decisions, and validation gate before writing final requirements text.
   - Identify the uncertainties that would materially change this frame.
   - Do not write requirements as settled when the user has not confirmed the key fork.

6. **Run structured confirmation**
   - Ask at most 5 rounds of confirmation questions for the basic uncertainties.
   - Ask exactly one highest-leverage question per round.
   - Provide 2-3 concrete answer choices and mark the recommended answer first.
   - Stop after the question and wait for the user's answer.
   - After each answer, update the requirement frame and decide whether another question is still necessary.

7. **Run Less Dumb Challenge**
   - Critique the clarified requirement after the requirement frame exists; do not use this as a normal question-generation step.
   - Challenge up to 3 questionable points from whole-project and deep-design perspectives.
   - Tie every challenge to evidence; do not challenge just to sound skeptical.
   - State whether the issue lives in the requirement, product description, workflow, data model, architecture, UX, operational model, or validation gate.
   - State why the point may be unwise, what impact it creates, and what better framing should replace or constrain it.
   - Do not remove scope in this stage; mark questionable scope as needs confirmation, candidate non-goal, or better-framed requirement.

8. **Make the requirement less wrong**
   - Identify the real user, business, or workflow problem.
   - Separate goal, proposed solution, assumptions, constraints, and success criteria.
   - Challenge requirements that look like copied process, premature automation, excessive configurability, or implementation detail disguised as product need.

9. **Update the requirements document**
   - Record current understanding, customer goal, scope, non-goals, evidence, open questions, decisions, and validation gate.
   - Preserve previous decisions unless current evidence contradicts them; when they change, add a short change-log entry.
   - Record Less Dumb Challenge findings separately from clarification questions.
   - Keep implementation details out unless they are evidence for the requirement.

10. **Reduce to a validation demo**
   - Define the smallest artifact that can test the real need: demo, mock, manual workflow, test case, PRD slice, prototype, or decision memo.
   - Explicitly list non-goals.
   - Defer details that do not affect the next decision.

11. **Set the decision gate**
   - Define what would prove the demo is enough.
   - Define what evidence would force a revision or rejection.

## References

- Read `references/evidence-floor.md` when the request touches a repository, product surface, workflow, or existing project and evidence is thin.
- Read `references/hypothesis-quality.md` before giving medium or high confidence, or when the user challenges shallow inference.
- Read `references/requirements-document.md` before creating, selecting, or updating files under `docs/requirements/`.
- Read `references/structured-confirmation.md` before asking the user to confirm scope, goal, non-goals, validation gates, or unresolved requirement forks.
- Read `references/less-dumb-challenge.md` before writing requirements as settled, especially when a point may be overbuilt, misframed, operationally heavy, low-value, or inconsistent with the project as a whole.

## Output

Use this compact structure:

```text
Evidence inspected:
- Working path:
- Project map:
- Requirement docs read/updated:
- Docs read:
- Code/workflow paths checked:
- Conversation facts used:
- Missing evidence:

Working hypothesis:
- User probably wants:
- Real problem:
- Evidence sentence:
- Would be wrong if:
- Suspicious assumptions:
- Requirement frame:
- Less Dumb Challenge:
- Keep:
- Questionable or candidate non-goals:
- Minimum demo:
- Non-goals:
- Validation gate:
- Confirmed decisions:
- Open questions:
- Confidence:
- Blocking questions, if any:
```

## Stop Conditions

- If only conversation history was inspected, confidence cannot exceed medium; say the hypothesis is provisional and list the missing project evidence.
- If a requirement is real enough to preserve, do not leave it only in chat; create or update the relevant `docs/requirements/` file.
- If key requirement forks remain unresolved after 5 confirmation rounds, preserve them as open questions instead of pretending the requirement is settled.
- If no evidence-backed Less Dumb Challenge exists, say so in the final answer and in the requirement document; do not invent objections.
- If the real problem cannot be inferred and the next step is irreversible, stop and ask the smallest set of blocking questions.
- If the request is trying to optimize, accelerate, or automate an unclear requirement, send the work back to this stage.
- If the user explicitly approves the hypothesis and demo gate, hand off to implementation or to the next Algorithm stage.
