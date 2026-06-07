---
name: 01-make-requirements-less-dumb
description: Pressure-test, clarify, and durably document rough product, engineering, workflow, PRD, issue, or feature requests before implementation. Use when a request is vague, overbuilt, assumption-heavy, solution-first, or when Codex needs to create or update docs/requirements, initialize Algorithm Stage Status in requirements-map.md, complete requirement clarification, and run a user-facing Less Dumb Challenge Dialogue before later Algorithm stages.
---

# Make Requirements Less Dumb

## Stage Objective

Turn a rough request into a durable requirements document and a validated working hypothesis. The goal is not to collect every possible requirement; the goal is to identify the real problem, expose questionable assumptions, update the right requirement file, and reduce the next step to a demo or decision gate.

## Core Rule

Read first. Infer next. Ask only if the answer changes the next action.

Do not make the user fill out a long questionnaire. Use the current conversation, repo docs, issues, product notes, screenshots, logs, and prior decisions before asking.

When a real requirement is discovered, preserve it in `docs/requirements/` so future sessions refine the same document instead of starting over.

Before asking requirement questions, infer the current Algorithm stage from evidence. If docs, plans, design, code, tests, or a demo show the requirement has already been clarified, update `Algorithm Stage Status` and move to the earliest unresolved gate instead of re-asking basic requirement questions.

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

Hard rule: structured confirmation and Less Dumb Challenge Dialogue are separate gates. Structured confirmation clarifies what the user wants and preserves it in requirements. Less Dumb Challenge Dialogue starts only after the requirement is marked clarified, and critiques whether the clarified requirement, description, workflow, data shape, or architecture is unreasonable, harmful, overbuilt, inconsistent, or solving the wrong problem.

Hard rule: the Less Dumb Challenge must be a user dialogue, not a field-labeled report. Think with structure internally, but speak in plain language with a clear point of view. If material challenges exist, discuss one challenge at a time, explain why it worries you, give your recommendation, invite pushback, then update the requirement document and `requirements-map.md`.

## Procedure

1. **Collect context**
   - Satisfy the Evidence Floor before judging.
   - Read local project guidance, current plans, issues, comments, screenshots, logs, or existing code paths that are directly relevant.
   - Prefer current source-of-truth files over memory or generic best practices.

2. **Find or create the requirements document**
   - Use `docs/requirements/requirements-map.md` as the navigation file.
   - Ensure `requirements-map.md` contains `Algorithm Stage Status`; initialize it if missing.
   - Use `docs/requirements/project-overview.md` for project-wide requirements.
   - Use `docs/requirements/<feature-or-domain>.md` for feature, workflow, or domain-specific requirements.
   - If the right document exists, update it instead of creating a duplicate.
   - Create files lazily only when there is a requirement worth recording.
   - Write requirements documents in English, even when chatting with the user in another language.

3. **Zoom out before judging**
   - If the area is unfamiliar, produce a short map first: domain objects, relevant modules or files, callers or workflow steps, source-of-truth documents, and unknown surfaces.
   - Use project vocabulary rather than generic labels.
   - If no project files or artifacts are available, say so and downgrade confidence.

4. **Infer current Algorithm stage**
   - Read `references/stage-inference.md`.
   - Compare `Algorithm Stage Status` with evidence from requirement docs, plans, design docs, implementation, tests, demos, screenshots, and current user feedback.
   - If evidence shows requirement clarification has already happened, mark `Requirement Clarification` as `Clarified` and record the evidence.
   - If a demo or implementation already exists, do not ask basic V1 positioning, user, or scope questions unless docs and implementation conflict.
   - Move to the earliest unresolved gate: structured confirmation only when clarification is truly unresolved; otherwise Less Dumb Challenge Dialogue, then 02.

5. **Form a falsifiable working hypothesis**
   - State what the user probably wants.
   - State what the request is probably not asking for.
   - Name the most suspicious part of the proposed requirement.
   - Include the evidence sentence: "I believe the real requirement is X because evidence A/B/C."
   - State what evidence would disprove or change the hypothesis.

6. **Build the requirement frame**
   - Draft the customer goal, scope, non-goals, evidence, open questions, decisions, and validation gate before writing final requirements text.
   - Identify the uncertainties that would materially change this frame.
   - Do not write requirements as settled when the user has not confirmed the key fork.

7. **Run structured confirmation only if needed**
   - Mark `Requirement Clarification` as `In Progress` in `requirements-map.md` while material clarification questions remain.
   - Skip this step when stage inference shows requirement clarification is already `Clarified`.
   - Ask at most 5 rounds of confirmation questions for the basic uncertainties.
   - Ask exactly one highest-leverage question per round.
   - Provide 2-3 concrete answer choices and mark the recommended answer first.
   - Stop after the question and wait for the user's answer.
   - After each answer, update the requirement frame and decide whether another question is still necessary.

8. **Mark requirement clarification complete**
   - When there are no material clarification questions left, update the requirement document and mark `Requirement Clarification` as `Clarified` in `requirements-map.md`.
   - If stage inference already proves clarification is complete, mark it `Clarified` with an evidence note instead of asking confirmation questions.
   - Set `Current recommended skill` to `01-make-requirements-less-dumb` when `Less Dumb Challenge Dialogue` is not yet `Resolved`.
   - If later user input changes the requirement, mark `Requirement Clarification` as `Reopened` and record why.

9. **Run Less Dumb Challenge Dialogue**
   - Start only after `Requirement Clarification` is `Clarified`.
   - Mark `Less Dumb Challenge Dialogue` as `In Progress` in `requirements-map.md` while discussing material challenges.
   - Critique the clarified requirement after the requirement frame exists; do not use this as a normal question-generation step or as a report-only section.
   - Do not use table-like labels in user-facing challenge text. Avoid rigid lines like `Target`, `Questionable point`, `Evidence`, `Options`.
   - Challenge up to 3 questionable points from whole-project and deep-design perspectives.
   - Tie every challenge to evidence; do not challenge just to sound skeptical.
   - State whether the issue lives in the requirement, product description, workflow, data model, architecture, UX, operational model, or validation gate.
   - State why the point may be unwise, what impact it creates, and what better framing should replace or constrain it.
   - Present one material challenge at a time as a short natural-language discussion: "I am worried about X because Y. I would handle it by Z."
   - Do not ask requirement-clarification questions during this stage. If the challenge depends on an unresolved positioning, scope, user, or validation fork, mark `Requirement Clarification` as `Reopened` and return to structured confirmation.
   - Do not default to multiple-choice options in this stage. Use options only when the user must choose between concrete requirement changes.
   - Do not remove scope in this stage; mark questionable scope as needs confirmation, candidate non-goal, or better-framed requirement.
   - After the user resolves all material challenges, update the requirement document and mark `Less Dumb Challenge Dialogue` as `Resolved`.

10. **Make the requirement less wrong**
   - Identify the real user, business, or workflow problem.
   - Separate goal, proposed solution, assumptions, constraints, and success criteria.
   - Challenge requirements that look like copied process, premature automation, excessive configurability, or implementation detail disguised as product need.

11. **Update the requirements document**
   - Record current understanding, customer goal, scope, non-goals, evidence, open questions, decisions, and validation gate.
   - Preserve previous decisions unless current evidence contradicts them; when they change, add a short change-log entry.
   - Record Less Dumb Challenge findings separately from clarification questions.
   - Update `Algorithm Stage Status` in `requirements-map.md` every time the requirement is clarified, reopened, challenged, or resolved.
   - Keep implementation details out unless they are evidence for the requirement.

12. **Reduce to a validation demo**
   - Define the smallest artifact that can test the real need: demo, mock, manual workflow, test case, PRD slice, prototype, or decision memo.
   - Explicitly list non-goals.
   - Defer details that do not affect the next decision.

13. **Set the decision gate**
   - Define what would prove the demo is enough.
   - Define what evidence would force a revision or rejection.

## References

- Read `references/evidence-floor.md` when the request touches a repository, product surface, workflow, or existing project and evidence is thin.
- Read `references/hypothesis-quality.md` before giving medium or high confidence, or when the user challenges shallow inference.
- Read `references/requirements-document.md` before creating, selecting, or updating files under `docs/requirements/`.
- Read `references/stage-inference.md` before asking requirement questions when docs, plans, implementation, tests, demos, or user feedback may show the work is already past clarification.
- Read `references/structured-confirmation.md` before asking the user to confirm scope, goal, non-goals, validation gates, or unresolved requirement forks.
- Read `references/less-dumb-challenge.md` before writing requirements as settled, especially when a point may be overbuilt, misframed, operationally heavy, low-value, or inconsistent with the project as a whole.

## Output

Use this compact structure:

```text
Evidence inspected:
- Working path:
- Project map:
- Requirement docs read/updated:
- Algorithm Stage Status:
- Stage inference:
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
- If `requirements-map.md` exists but lacks `Algorithm Stage Status`, add it before advancing.
- If stage inference shows requirement clarification is already complete, mark `Requirement Clarification` as `Clarified` and do not ask basic requirement questions.
- If key requirement forks remain unresolved after 5 confirmation rounds, preserve them as open questions instead of pretending the requirement is settled.
- If no evidence-backed Less Dumb Challenge exists, say so in the final answer and in the requirement document, then mark `Less Dumb Challenge Dialogue` as `Resolved`; do not invent objections.
- If the real problem cannot be inferred and the next step is irreversible, stop and ask the smallest set of blocking questions.
- If the request is trying to optimize, accelerate, or automate an unclear requirement, send the work back to this stage.
- If the user explicitly approves the hypothesis and demo gate, hand off to implementation or to the next Algorithm stage.
