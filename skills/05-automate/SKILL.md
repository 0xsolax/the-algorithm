---
name: 05-automate
description: Decide whether and how to automate a stable, validated, deleted, optimized, and accelerated workflow. Use when a repeated product, engineering, operations, QA, release, reporting, or agent workflow is ready for automation, or when a user asks to script, schedule, agentize, integrate, or remove manual work from a process.
---

# Automate

## Stage Objective

Automate only what is stable enough to trust. The goal is to remove repeated manual work without automating unclear requirements, unnecessary steps, broken quality, or unmeasured bottlenecks.

## Core Rule

Automation is last. If a step should be deleted, do not automate it. If a step is unstable, do not automate it yet.

## Question Budget

- Ask 0-2 questions by default.
- Ask only about irreversible effects, credentials, permissions, schedules, rollback, or human approval gates.
- Do not ask for implementation preferences until the automation gate passes.

## Procedure

1. **Run the automation gate**
   - Requirement is validated.
   - Unnecessary parts are deleted.
   - Remaining workflow is optimized.
   - Acceleration pass is complete, or evidence shows no acceleration is needed.
   - Bottlenecks are understood with a baseline or deliberate skip reason.
   - Inputs, outputs, failure modes, owners, and rollback are clear.
   - If any item fails, return to the relevant earlier Algorithm stage.

2. **Classify the manual work**
   - Repeated transformation
   - Repeated check
   - Repeated notification
   - Repeated deployment or release step
   - Repeated data movement
   - Repeated agent reasoning pattern

3. **Choose the smallest automation**
   - Prefer a checklist, command, script, test, saved prompt, or one-shot tool before a scheduler, service, agent, or integration.
   - Keep a manual override.
   - Keep logs or artifacts that prove what happened.

4. **Design failure handling**
   - Define what happens on partial failure.
   - Define who is notified.
   - Define what can be retried safely.
   - Define what must require human approval.

5. **Verify automation**
   - Run a dry run when possible.
   - Test happy path, invalid input, permission failure, repeated run, and rollback.
   - Confirm the automation saves time without reducing correctness or visibility.

## References

- Read `references/automation-gate.md` before automating workflows that touch external systems, credentials, production data, scheduling, notifications, or irreversible actions.

## Output

Use this compact structure:

```text
Automation pass:
- Stable workflow:
- Automation gate:
- Acceleration evidence:
- Manual work to remove:
- Smallest automation:
- Human approval gate:
- Failure handling:
- Dry-run or test plan:
- Rollback:
- Blocking questions, if any:
```

## Stop Conditions

- If the workflow is not stable, do not automate. Return to the earliest failing Algorithm stage.
- If automation needs secrets, production permissions, scheduled execution, or external accounts, list dependencies and stop for approval before changing external state.
- If automation makes the process harder to inspect or reverse, choose a smaller automation.
