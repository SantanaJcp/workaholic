# Workaholic Prompt Pack

Reusable prompts for operating Workaholic as an Engram-first Delivery Operating System.

## How to Use

Use one prompt at a time. Do not paste the whole pack into a thread. Load the smallest prompt that matches the current job so the agent keeps clean context.

## Prompt Order

1. `01-intake-raw-capture.md` — save raw input before analysis or execution.
2. `02-normalize-work-item.md` — enrich a raw capture from Engram and create/update a work-item.
3. `03-chief-of-staff-heartbeat.md` — review active work and surface decisions, blockers, risks, and progress.
4. `04-daily-report.md` — generate the daily decision report from Engram records.
5. `05-worker-handoff.md` — prepare a bounded execution prompt for a worker thread.
6. `06-closeout-learning.md` — close work and capture lessons after delivery.

## Research-Backed Principles

- Keep persistent rules in `AGENTS.md`; Codex reads them before work starts. Source: OpenAI Codex AGENTS.md guide — https://developers.openai.com/codex/guides/agents-md
- Use Codex customization layers intentionally: project guidance, memories, skills, MCP, and subagents each solve different problems. Source: OpenAI Codex customization — https://developers.openai.com/codex/concepts/customization
- Prefer simple, explicit workflows before autonomous agents. Prompt chaining, routing, orchestrator-worker, and evaluator patterns are useful when they match the task shape. Source: Anthropic Building Effective Agents — https://www.anthropic.com/research/building-effective-agents
- Keep human approval for sensitive or irreversible actions. Source: OpenAI Agents SDK human-in-the-loop — https://openai.github.io/openai-agents-python/human_in_the_loop/
- Use handoffs only when specialization or context isolation is valuable. Source: OpenAI Agents SDK handoffs — https://openai.github.io/openai-agents-python/handoffs/
- Start complex work with planning and re-plan when work goes sideways. Source: Claude Code power user tips — https://support.claude.com/en/articles/14554000-claude-code-power-user-tips
- Avoid context pollution. Community reports consistently warn that one giant Chief of Staff thread becomes noisy; route and summarize instead of dumping logs. Source example: Reddit discussion — https://www.reddit.com/r/ClaudeAI/comments/1uju6d4/claude_code_for_ai_chief_of_staff_multiple_agents/
- Build the workflow first; dashboards and integrations come later. Source example: Reddit multi-agent operations discussion — https://www.reddit.com/r/AI_Agents/comments/1s7bwgx/3_weeks_running_6_ai_agents_247_heres_what_id/

## Workaholic Defaults

- Engram is operational state.
- Git is system definition.
- Raw input must become an Engram `raw_capture` before planning or execution.
- Work must be represented by a canonical Engram `work_item`.
- Status changes, blockers, decisions, reports, and lessons are Engram records.
- The user remains director: approvals, commitments, cancellation, and delivery decisions stay with the user unless delegation level changes later.
