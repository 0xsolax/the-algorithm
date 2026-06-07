# The Algorithm Skills

Agent skills based on Elon Musk's five-step engineering algorithm:

1. Make the requirements less dumb.
2. Delete the part or process step.
3. Optimize.
4. Accelerate.
5. Automate.

This repository turns that sequence into installable agent skills for product and engineering work. The current focus is **01 Make Requirements Less Dumb**. The remaining skills are present as early scaffolds and will be refined after the requirement stage is stable.

## Current Status

| Skill | Status | Notes |
| --- | --- | --- |
| `01-make-requirements-less-dumb` | Primary / usable | Clarifies requirements, writes durable requirement docs, and runs a separate Less Dumb Challenge before implementation. |
| `02-delete-the-part-or-process-step` | Draft | Intended for removing unjustified scope after requirements are clear. |
| `03-optimize` | Draft | Intended for improving the validated remaining scope. |
| `04-accelerate` | Draft | Intended for speeding up stable workflows after optimization. |
| `05-automate` | Draft | Intended for automation only after the workflow is stable, validated, optimized, and measurable. |

## Install

Install all skills globally for Codex:

```bash
npx skills add 0xsolax/the-algorithm -a codex -g -y
```

Install only the current primary skill:

```bash
npx skills add 0xsolax/the-algorithm --skill 01-make-requirements-less-dumb -a codex -g -y
```

Install all skills globally for Claude Code:

```bash
npx skills add 0xsolax/the-algorithm -a claude-code -g -y
```

Test a local checkout:

```bash
npx skills add . --list
```

## What 01 Does

`01-make-requirements-less-dumb` helps an agent handle rough product, engineering, workflow, PRD, issue, or feature requests before implementation.

It guides the agent to:

- inspect the real project context before judging,
- avoid long questionnaires,
- ask only high-leverage confirmation questions,
- preserve requirements in `docs/requirements/`,
- separate clarification from criticism,
- run a visible `Less Dumb Challenge`,
- reduce the next step to a demo or decision gate.

### Execution Model

1. **Read first**
   - Confirm the working path.
   - Inspect source-of-truth files such as README, AGENTS/CLAUDE, rules, guides, plans, design docs, issues, screenshots, and relevant code paths.
   - Do not make confident project-level judgments from chat history alone.

2. **Build a requirement frame**
   - Identify the likely user goal, real problem, scope, non-goals, evidence, decisions, open questions, and validation gate.
   - Keep the frame falsifiable: state what evidence would change the conclusion.

3. **Ask structured confirmation questions**
   - Ask at most five rounds.
   - Ask one question per round.
   - Provide a recommended answer and 2-3 concrete choices.
   - Use questions to clarify what the user means and what should be written into the requirement document.

4. **Update durable requirement docs**
   - Use this target-project structure:

```text
docs/
  requirements/
    requirements-map.md
    project-overview.md
    <feature-or-domain>.md
```

   - Write requirement documents in English, even when the conversation is in another language.
   - Update the existing feature document instead of regenerating a new one each time.

5. **Run Less Dumb Challenge**
   - This is separate from confirmation.
   - Confirmation asks: "What does the user mean?"
   - Less Dumb Challenge asks: "Now that the requirement is clear, is any part of it unreasonable, misframed, internally inconsistent, overbuilt, or architecturally wrong?"

   The challenge uses two lenses:

   - **Whole-project lens**: project boundary, business value, workflow duplication, source-of-truth conflicts, operational cost, rollout risk, stage mismatch.
   - **Deep-design lens**: requirement wording, domain model, data identity, ownership, lifecycle, architecture coupling, permissions, UX labels, edge cases, and validation quality.

6. **Define the next gate**
   - Produce the minimum demo, prototype, decision memo, or validation artifact needed before moving to design or implementation.

## Repository Structure

```text
skills/
  01-make-requirements-less-dumb/
    SKILL.md
    agents/openai.yaml
    references/
      evidence-floor.md
      hypothesis-quality.md
      requirements-document.md
      structured-confirmation.md
      less-dumb-challenge.md

  02-delete-the-part-or-process-step/
  03-optimize/
  04-accelerate/
  05-automate/
```

## 中文说明

这个仓库把 Elon Musk 常说的五步工程流程做成一组 agent skills：

1. 让需求不那么蠢
2. 删除不必要的部分或流程
3. 优化
4. 加速
5. 自动化

当前重点是 **01 Make Requirements Less Dumb**。它已经是主要可用版本。`02-05` 目前还是初版框架，后续会在 `01` 稳定后继续完善。

## 当前状态

| Skill | 状态 | 说明 |
| --- | --- | --- |
| `01-make-requirements-less-dumb` | 主要可用 | 负责梳理需求、维护需求文档，并在实现前做独立的 Less Dumb Challenge。 |
| `02-delete-the-part-or-process-step` | 初稿 | 用于在需求明确后删除不必要范围。 |
| `03-optimize` | 初稿 | 用于优化已经验证且保留下来的范围。 |
| `04-accelerate` | 初稿 | 用于在系统和流程稳定后做加速。 |
| `05-automate` | 初稿 | 用于在流程稳定、可验证、可观测之后再自动化。 |

## 安装

安装全部 skills 到 Codex：

```bash
npx skills add 0xsolax/the-algorithm -a codex -g -y
```

只安装目前最主要的 `01`：

```bash
npx skills add 0xsolax/the-algorithm --skill 01-make-requirements-less-dumb -a codex -g -y
```

安装到 Claude Code：

```bash
npx skills add 0xsolax/the-algorithm -a claude-code -g -y
```

本地检查：

```bash
npx skills add . --list
```

## 01 会怎样引导 Agent

`01-make-requirements-less-dumb` 的目标不是帮用户堆功能列表，而是让 agent 像需求负责人一样工作：

- 先读真实项目上下文，而不是只看聊天记录；
- 根据文档、代码、页面、流程和用户描述形成需求框架；
- 少问问题，只问会改变需求方向的关键问题；
- 把需求沉淀到目标项目的 `docs/requirements/`；
- 把“确认需求”和“质疑需求”分开；
- 独立执行 `Less Dumb Challenge`；
- 最后收束成最小 demo 或决策门槛。

### 执行流程

1. **先查证据**
   - 确认当前项目路径。
   - 阅读 README、AGENTS/CLAUDE、规则、指南、计划、设计稿、issue、截图和相关代码路径。
   - 如果只看了聊天记录，不能给出高置信度判断。

2. **形成需求框架**
   - 梳理用户目标、真实问题、范围、非目标、证据、已确认决策、开放问题和验证门槛。

3. **结构化确认**
   - 最多 5 轮。
   - 每轮只问一个问题。
   - 给出推荐选项和 2-3 个具体选择。
   - 提问的目的只是明确需求，并写入需求文档。

4. **维护需求文档**
   - 在目标项目里维护：

```text
docs/
  requirements/
    requirements-map.md
    project-overview.md
    <feature-or-domain>.md
```

   - 文档正文使用英文。
   - 同一个功能持续更新同一份文档，不每次重新生成。

5. **执行 Less Dumb Challenge**
   - 这是独立质疑环节，不是提问技巧。
   - 它会从两层看问题：
     - **大局观**：这个功能放在整个项目里是否合理，是否重复，是否阶段错误，是否运营成本过高。
     - **深层设计**：需求描述、领域模型、数据身份、权限、架构耦合、UX 文案、边界条件、验证门槛是否有设计错误。

6. **定义下一步门槛**
   - 给出最小 demo、原型、决策 memo 或验证标准。
   - 没有通过这个门槛前，不应该直接进入实现、优化、加速或自动化。

## Notes

This repository is intentionally conservative. It should help agents slow down at the beginning, preserve the customer's real intent, challenge weak assumptions, and avoid optimizing or automating the wrong thing.

## Maintainer

Solazhu
