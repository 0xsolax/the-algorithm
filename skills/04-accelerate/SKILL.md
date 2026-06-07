---
name: 04-accelerate
description: Speed up a stable and optimized product, engineering workflow, code path, delivery process, feedback loop, or operational system. Use only after the goal is clear, unnecessary parts are deleted, and the remaining work is fit-for-purpose; focuses on measured bottlenecks in response time, cycle time, throughput, iteration speed, handoffs, or feedback latency.
---

# Accelerate

## Stage Objective

Make a stable system faster without changing what it is for. Acceleration can target software performance, delivery speed, decision latency, feedback loops, operations, or human workflow throughput.

## Core Rule

Never speed up a broken, unclear, or overbuilt process. Acceleration multiplies both value and waste.

## Question Budget

- Ask 0-2 questions by default.
- Ask only when the target speed metric, acceptable tradeoff, or bottleneck ownership cannot be inferred.
- Do not ask "what should be faster?" if logs, traces, tests, delivery history, or workflow evidence can show it.

## Procedure

1. **Confirm readiness**
   - Requirement is clear.
   - Unnecessary parts are removed.
   - Remaining solution is optimized for purpose.
   - If any condition fails, return to the earlier Algorithm stage.

2. **Define the speed metric**
   - Choose one primary metric: response time, build time, release cycle, review loop, handoff delay, task duration, queue depth, error recovery time, or similar.
   - Record the current baseline when possible.

3. **Find the bottleneck with evidence**
   - Use logs, profiling, test timing, traces, user journey timing, process timestamps, issue history, or manual observation.
   - Separate perceived slowness from measured bottleneck.

4. **Accelerate the narrowest constraint**
   - Remove waiting, batching, repeated work, serial handoffs, unnecessary round trips, expensive queries, oversized payloads, redundant validation, or unclear ownership.
   - Prefer changes that improve feedback speed before adding complex infrastructure.
   - Do not add caching, concurrency, queues, or background jobs without proving they address the bottleneck.

5. **Verify speed and damage**
   - Compare before and after.
   - Check correctness, observability, rollback, and user-visible behavior.
   - State any tradeoff created by acceleration.

## References

- Read `references/measurement-rubric.md` when there is no baseline, when the bottleneck is disputed, or before adding caching, concurrency, queues, background jobs, or process automation for speed.

## Output

Use this compact structure:

```text
Acceleration pass:
- Stable target:
- Speed metric:
- Baseline:
- Bottleneck evidence:
- Narrowest acceleration:
- Tradeoff:
- Verification:
- Rollback:
- Blocking questions, if any:
```

## Stop Conditions

- If there is no baseline or observable bottleneck, first add measurement or run a short observation pass.
- If speeding up requires changing the validated goal, return to `make-requirements-less-dumb`.
- If the speedup would hide failures or weaken correctness, reject it or return to `optimize`.
