---
name: 04-accelerate
description: Speed up a stable and optimized product, engineering workflow, code path, delivery process, feedback loop, or operational system. Use only after the goal is clear, unnecessary parts are deleted, and the remaining work is fit-for-purpose; focuses on measured bottlenecks in response time, cycle time, throughput, iteration speed, handoffs, or feedback latency.
---

# Accelerate

## Stage Objective

Make a stable system faster without changing what it is for. Acceleration can target software performance, delivery speed, decision latency, feedback loops, operations, or human workflow throughput.

## Core Rule

Never speed up a broken, unclear, or overbuilt process. Acceleration multiplies both value and waste.

Read `docs/requirements/requirements-map.md` before starting. Use `Algorithm Stage Status` to confirm earlier gates are complete, and update `Acceleration Pass` as measurement and acceleration progress.

## Question Budget

- Ask 0-2 questions by default.
- Ask only when the target speed metric, acceptable tradeoff, or bottleneck ownership cannot be inferred.
- Do not ask "what should be faster?" if logs, traces, tests, delivery history, or workflow evidence can show it.

## Procedure

1. **Confirm readiness**
   - Read `Algorithm Stage Status` in `docs/requirements/requirements-map.md`.
   - `Requirement Clarification` is `Clarified`.
   - `Less Dumb Challenge Dialogue` is `Resolved`.
   - `Stable Version Boundary` is `Confirmed`.
   - `Optimization Pass` is `Confirmed`.
   - If any condition fails, return to the earlier Algorithm stage.

2. **Define the speed metric**
   - Choose one primary metric: response time, build time, release cycle, review loop, handoff delay, task duration, queue depth, error recovery time, or similar.
   - Record the current baseline when possible.
   - Mark `Acceleration Pass` as `Measured` when the baseline or deliberate measurement skip reason is recorded.

3. **Find the bottleneck with evidence**
   - Use logs, profiling, test timing, traces, user journey timing, process timestamps, issue history, or manual observation.
   - Separate perceived slowness from measured bottleneck.

4. **Accelerate the narrowest constraint**
   - Mark `Acceleration Pass` as `In Progress` when acceleration work starts.
   - Remove waiting, batching, repeated work, serial handoffs, unnecessary round trips, expensive queries, oversized payloads, redundant validation, or unclear ownership.
   - Prefer changes that improve feedback speed before adding complex infrastructure.
   - Do not add caching, concurrency, queues, or background jobs without proving they address the bottleneck.

5. **Verify speed and damage**
   - Compare before and after.
   - Check correctness, observability, rollback, and user-visible behavior.
   - State any tradeoff created by acceleration.
   - Mark `Acceleration Pass` as `Confirmed` after speed and damage checks pass, and set `Current recommended skill` to `05-automate`.

## References

- Read `references/measurement-rubric.md` when there is no baseline, when the bottleneck is disputed, or before adding caching, concurrency, queues, background jobs, or process automation for speed.

## Output

Use this compact structure:

```text
Acceleration pass:
- Algorithm Stage Status:
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
- If `Algorithm Stage Status` is missing from `requirements-map.md`, return to `01-make-requirements-less-dumb` to initialize it.
- If `Algorithm Stage Status` shows 01, 02, or 03 unresolved, return to the earliest unresolved stage.
- If speeding up requires changing the validated goal, return to `make-requirements-less-dumb`.
- If the speedup would hide failures or weaken correctness, reject it or return to `optimize`.
