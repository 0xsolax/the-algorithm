# Stable Version

Use this reference before claiming the deletion pass has produced a stable version.

## Definition

A stable version is the smallest surviving requirement, workflow, product surface, or implementation that still satisfies the validated goal and can be regression-checked.

It is not the "best" version, the most polished version, or the most complete version. Optimization comes later.

## Stable Version Shape

```text
Stable version:
- Goal it still satisfies:
- Included:
- Intentionally absent:
- Manual steps accepted for now:
- Existing capabilities reused:
- New parts still justified:
- Re-entry triggers for deferred parts:
- Regression checks:
- Add-back risk:
```

## What To Remove From The Stable Version

Remove or defer:

- broad dashboards when the demo only needs one workflow,
- extra tabs that do not prove the validation gate,
- free-form configuration before one fixed path is validated,
- second storage or source-of-truth models,
- speculative statuses and lifecycle fields,
- premature shared abstractions,
- automation around an unstable manual process,
- optional integrations that can be represented by a manual or imported artifact,
- polishing work that belongs to `03-optimize`,
- speed work that belongs to `04-accelerate`,
- automation work that belongs to `05-automate`.

## Regression Checks

Every stable version needs checks that prove deletion did not damage the real goal.

Examples:

- requirement doc still satisfies the customer goal and validation gate,
- core happy path still works,
- required permissions still block or allow the right users,
- required records still display and save correctly,
- no removed field or state is referenced by active UI, API, tests, docs, or workflow notes,
- manual substitute is documented when automation is deferred,
- deleted/deferred items have clear re-entry triggers if they may return.

## Add-Back Risk

Name the risk of deleting or deferring:

- `Low`: easy to add back, no data migration, no user promise broken.
- `Medium`: may require UI/API changes but no irreversible data loss.
- `High`: affects data model, permissions, compliance, reporting, or committed customer behavior.

High add-back risk usually needs user confirmation before deletion.
