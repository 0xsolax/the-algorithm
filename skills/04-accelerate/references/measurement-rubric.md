# Measurement Rubric

Use this reference before accelerating a stable system or workflow.

## Baseline First

Do not speed up without naming the metric:

```text
Metric:
- Current baseline:
- Target or desired direction:
- Evidence source:
- Bottleneck:
- Tradeoff:
```

Acceptable evidence includes logs, traces, profiler output, test timing, build timing, issue timestamps, review cycle history, queue depth, manual stopwatch observations, or user journey timing.

## Bottleneck Types

- Runtime: slow query, large payload, render cost, cold start, network round trip.
- Delivery: slow build, slow test, unclear review path, release batching.
- Workflow: repeated handoff, waiting for approval, duplicated data entry, unclear owner.
- Feedback: slow error discovery, missing checks, late user validation.

## Acceleration Choices

Prefer:

- Remove waits, duplicate work, and unnecessary handoffs.
- Narrow payloads, queries, and validation surfaces.
- Improve feedback speed before adding infrastructure.
- Add measurement if no baseline exists.

Be skeptical of:

- Caching without invalidation clarity.
- Concurrency without ordering guarantees.
- Queues without failure handling.
- Background jobs that hide user-visible failure.
- Automation used as a substitute for deletion.

## Verification

Compare before and after, then check damage:

- Correctness unchanged.
- Failure modes visible.
- Rollback known.
- User-facing behavior acceptable.
