# Hypothesis Quality

Use this reference before giving medium or high confidence, or when the user says the agent is guessing too quickly.

## Required Shape

A good requirement hypothesis is falsifiable:

```text
I believe the real requirement is [X] because [evidence A], [evidence B], and [evidence C].
This would be wrong if [specific disconfirming evidence].
```

Avoid vague claims such as "the user probably wants better UX" or "this seems like a workflow issue" unless they are tied to evidence.

## Quality Gate

Before output, answer:

1. What concrete evidence supports this interpretation?
2. What alternative interpretation did you reject?
3. What would change the next action?
4. What can be safely deferred?
5. What is the smallest demo or decision gate?

If these answers are weak, lower confidence and ask at most 1-3 targeted questions.

## Suspicion Patterns

Challenge requirements that look like:

- A requested solution without the underlying problem.
- Automation of an unstable process.
- Configuration for a single known case.
- A copied enterprise workflow with no current user.
- A feature that compensates for unclear ownership.
- A request to optimize before deleting unnecessary steps.

## Output Discipline

Keep the output decisive but humble:

- Say what you believe.
- Say why.
- Say what would disprove it.
- Ask only the blocking questions.
