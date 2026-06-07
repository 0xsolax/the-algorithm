# Optimization Rubric

Use this reference when choosing what to improve after deletion.

## Optimization Order

1. Simplify the shape.
2. Fix correctness.
3. Improve user fit and information structure.
4. Improve maintainability.
5. Improve edge cases and error handling.
6. Leave speed to the acceleration stage unless speed is the quality defect.

## Choose One Dominant Target

Pick one target for the pass:

```text
Target:
- Why this target matters to the validated goal:
- Current weakness:
- Proposed smallest improvement:
- What is deliberately not optimized:
- Acceptance check:
```

## Good Optimization

- Makes the remaining scope easier to understand or use.
- Strengthens correctness without adding speculative features.
- Uses existing project patterns.
- Adds tests or acceptance checks proportional to risk.
- Removes incidental complexity before adding structure.

## Bad Optimization

- Adds configurability for a single case.
- Polishes deleted or deferred scope.
- Introduces a new abstraction without repeated use.
- Changes public behavior without an acceptance gate.
- Chases speed before quality is stable.

## Tradeoff Test

Before proposing the improvement, ask:

- Does this improve the validated goal or only the implementation taste?
- Does this make the next stage easier?
- Could the same gain come from deletion instead?
