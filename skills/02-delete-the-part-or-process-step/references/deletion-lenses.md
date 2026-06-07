# Deletion Lenses

Use these lenses after the validated goal and relevant surface have been inspected. The goal is to find parts that can be deleted, deferred, or collapsed because they do not serve the stable version.

## Whole-Project Lens

Look for deletion opportunities at the project, product, and enterprise level:

- Project boundary: the part belongs to another module, phase, team, or product.
- Business value: the part does not help the real customer, operator, or workflow goal.
- Workflow duplication: the part recreates an existing process, page, approval, upload area, report, or checklist.
- Source-of-truth conflict: the part creates a second place to store, edit, decide, approve, or interpret the same thing.
- Stage mismatch: the part belongs to optimize, accelerate, or automate, but the requirement is still being validated.
- Operational cost: the part requires permissions, maintenance, training, cleanup, governance, support, or monitoring before value is proven.
- Rollout risk: the part broadens the first release enough that the validation gate becomes noisy.
- Future speculation: the part exists only because "we may need it later".

## Deep-Design Lens

Look for deletion opportunities inside the requirement, design, workflow, or implementation:

- Field without lifecycle: a field has no clear creation, edit, ownership, display, or retirement rule.
- Redundant state: two statuses, tags, flags, tabs, or steps represent the same decision.
- Copied shape: a page, panel, or workflow was copied from another domain even though the data model differs.
- Premature abstraction: a shared component, adapter, framework, config, or extension point exists before two real uses prove it.
- Wrong coupling: deleting or changing one domain would unexpectedly break another domain.
- API/UI overreach: an API, table, filter, button, or tab exists only to make the screen look complete.
- Permission overreach: the design adds roles, approvals, or security paths before the core workflow is validated.
- Automation too early: a script, scheduler, integration, or agent flow automates unstable manual work.
- Validation noise: the part makes the demo bigger but does not help prove the real need.

## Evidence Standard

A deletion lens is not enough by itself. For every material candidate, cite at least one concrete evidence source:

- requirement doc or validation gate,
- prior Less Dumb Challenge,
- plan or design doc,
- code path, API, route, schema, component, caller, or test,
- current product behavior, screenshot, issue, or workflow artifact,
- confirmed user decision.

Do not propose deletion from taste, naming, or generic minimalism alone.
