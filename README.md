# The Algorithm Skills

Engineering workflow skills based on Elon Musk's five-step Algorithm:

1. Make the requirements less dumb.
2. Delete the part or process step.
3. Optimize.
4. Accelerate.
5. Automate.

This repository turns the sequence into reusable agent skills. The emphasis is context-first reasoning, low-question collaboration, deletion before optimization, and automation last.

## Skills

| Order | Skill | Purpose |
| --- | --- | --- |
| 01 | `01-make-requirements-less-dumb` | Clarify the real need, suspicious assumptions, minimum demo, non-goals, and validation gate. |
| 02 | `02-delete-the-part-or-process-step` | Remove unnecessary parts, process steps, abstractions, fields, handoffs, or features before improving them. |
| 03 | `03-optimize` | Simplify and improve the surviving scope for correctness, usability, maintainability, information structure, and edge cases. |
| 04 | `04-accelerate` | Speed up a stable system or workflow with evidence-backed bottleneck work. |
| 05 | `05-automate` | Automate only stable, validated, observable, and reversible workflows. |

## Install

Install all skills globally for Codex:

```bash
npx skills add solazhu/the-algorithm-skills -a codex -g -y
```

Install all skills globally for Claude Code:

```bash
npx skills add solazhu/the-algorithm-skills -a claude-code -g -y
```

Install one skill:

```bash
npx skills add solazhu/the-algorithm-skills --skill 01-make-requirements-less-dumb -a codex -g -y
```

Test a local checkout:

```bash
npx skills add . --list
```

## Design Notes

- Ask fewer questions by default. Read context, infer a working hypothesis, then ask only questions that change the next action.
- Each stage has a clear objective and a stop condition.
- Do not optimize what should be deleted.
- Do not accelerate unclear or broken workflows.
- Do not automate unstable work.

## Source Notes

This first version is based on the five-step formulation from Elon Musk's Starbase interview and later summaries of Walter Isaacson's description of "The Algorithm":

- [Everyday Astronaut: Starbase Tour and Interview with Elon Musk](https://everydayastronaut.com/starbase-tour-and-interview-with-elon-musk/)
- [Mint: Elon Musk's Lessons From Hell: Five Commandments for Business](https://www.livemint.com/special-report/elon-musk-s-lessons-from-hell-five-commandments-for-business/amp-11694529944885.html)

## Maintainer

Solazhu
