# Automation Gate

Use this reference before automating repeated work.

## Gate Checklist

Automation is allowed only when:

- Requirement is validated.
- Unnecessary parts are deleted.
- Remaining workflow is optimized.
- Acceleration pass is complete, or evidence shows no acceleration is needed.
- Inputs and outputs are stable.
- Failure modes are known.
- Owner and rollback are clear.
- Human approval boundaries are explicit.

If any item fails, return to the earliest failing Algorithm stage.

## Smallest Automation Ladder

Prefer the smallest useful automation:

1. Checklist or runbook.
2. Saved prompt or template.
3. One-shot command.
4. Script with dry run.
5. Test or CI check.
6. Scheduled job.
7. Service integration.
8. Autonomous agent workflow.

Do not jump to a later rung without explaining why earlier rungs are insufficient.

## Risk Classes

Stop for approval before changing external state when automation touches:

- Credentials or secrets.
- Production data.
- Payments, billing, email, notifications, or customer-visible actions.
- Scheduled execution.
- Destructive writes.
- Multi-account or third-party integrations.

## Verification

Before calling automation ready:

- Dry run exists or the lack of dry run is justified.
- Happy path tested.
- Invalid input tested.
- Permission failure tested.
- Repeated run is safe or blocked.
- Rollback is documented.
