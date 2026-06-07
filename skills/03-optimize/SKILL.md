---
name: 03-optimize
description: Simplify and optimize the remaining validated scope after deletion. Use when a feature, workflow, design, implementation, plan, prompt, or process already has a clear goal and reduced scope, and now needs better quality, usability, maintainability, correctness, information structure, edge-case handling, or fit-to-purpose without expanding scope or chasing speed first.
---

# Optimize

## Stage Objective

Make the surviving solution simpler and better for its validated purpose. Optimization here means better fit, correctness, usability, maintainability, and clarity. It does not mean acceleration yet.

## Core Rule

Optimize only what remains after deletion. Do not polish work that should not exist.

## Question Budget

- Ask 0-2 questions by default.
- Ask only when quality standards, user expectations, or acceptance criteria cannot be inferred from current context.
- Do not ask for broad preferences. Present a concrete optimization target and let the user correct it.

## Procedure

1. **Confirm the stable scope**
   - Restate the surviving feature, process, or implementation.
   - If deletion has not happened, run `delete-the-part-or-process-step` first.

2. **Simplify before local optimization**
   - Collapse redundant states, branches, UI choices, prompts, handoffs, or abstractions.
   - Prefer a clearer system-level shape before tuning a local part.
   - Do not optimize a local component in a way that makes the whole system worse.

3. **Identify optimization dimensions**
   - Correctness: Does it do the right thing under realistic inputs?
   - Usability: Is the workflow obvious and low-friction for the real user?
   - Maintainability: Is the implementation understandable and local?
   - Information structure: Is the right information visible at the right time?
   - Boundaries: Are failure cases, permissions, state, and data consistency handled?

4. **Choose one dominant optimization target**
   - Pick the target that most improves the validated goal.
   - Avoid parallel polishing across unrelated dimensions.
   - Name what will not be optimized in this pass.

5. **Make the smallest quality improvement**
   - Prefer local changes, clearer interfaces, better defaults, better validation, simpler copy, narrower state, or better test coverage.
   - Do not introduce generic abstractions for one use case.
   - Do not add configurability unless the validated goal requires it.

6. **Verify quality**
   - Define checks for happy path, error path, edge path, and regression risk.
   - For code, use existing test and build gates.
   - For UX or workflow, use manual acceptance checks tied to the real user task.

## References

- Read `references/optimization-rubric.md` when choosing the dominant optimization target, when optimization risks scope expansion, or when quality tradeoffs are unclear.

## Output

Use this compact structure:

```text
Optimization pass:
- Stable scope:
- Simplification:
- Dominant quality target:
- Current weakness:
- Proposed improvement:
- Not optimizing:
- Acceptance checks:
- Risk:
- Blocking questions, if any:
```

## Stop Conditions

- If the improvement expands the requirement, return to `make-requirements-less-dumb`.
- If the improvement preserves a part that should be removed, return to `delete-the-part-or-process-step`.
- If the main issue is speed or throughput rather than quality, move to `accelerate` only after the quality target is stable.
