# Evidence Floor

Use this reference when a request concerns an existing project, repo, workflow, product surface, or prior decision. The goal is to prevent chat-only conclusions.

## Minimum Evidence Ladder

1. **Path**: confirm `pwd` or repo root. If there is no repo, say so.
2. **Surface map**: list top-level files and directories; for large repos, map only relevant areas after search.
3. **Truth docs**: read README, AGENTS, CLAUDE, rules, guide, plan, design, issue, or product notes when present.
4. **Config and entrypoints**: read package/config/env schema/route/command files when implementation is involved.
5. **Relevant paths**: inspect callers, UI routes, API handlers, tests, workflows, or docs that directly touch the request.
6. **User context**: use conversation history as intent and constraint evidence, not as the only source of truth.

## Large Repo Rule

Do not read randomly. Build a map first:

```text
Project map:
- domain objects:
- source-of-truth docs:
- likely entrypoints:
- relevant modules:
- tests or verification surfaces:
- unknown surfaces:
```

Then read the smallest set of files that can confirm or reject the hypothesis.

## Confidence Rules

- **High**: current docs and relevant code/workflow evidence support the hypothesis; disconfirming evidence was named.
- **Medium**: source-of-truth docs were read but code/workflow evidence is incomplete.
- **Low**: only partial files, memory, or conversation evidence was inspected.
- **Provisional**: no project files or artifacts were available.

If only conversation history was inspected, confidence cannot exceed medium and should usually be low.

## Ask After Evidence

Ask the user only after evidence collection, and attach each question to a specific uncertainty:

```text
I found X in the project, but Y would change the demo scope. Which is true?
```
