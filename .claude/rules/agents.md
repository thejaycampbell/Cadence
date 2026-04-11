# Agent Orchestration

## Available Agents

Located in `.claude/agents/`:

| Agent | Purpose | When to Use |
|-------|---------|-------------|
| morning-orchestrator | Parallel morning dispatch | `/morning` command |
| calendar-briefer | Day schedule summary | Morning brief, prep |
| email-triager | Inbox prioritization | Morning brief |
| meeting-prepper | Research before calls | `/prep` command |
| researcher | Web research + synthesis | `/research` command |
| writer | Draft in user's voice | `/write` command |
| task-prioritizer | Score + sequence tasks | Morning brief, `/eod` |
| knowledge-updater | Extract session insights | `/eod`, `/weekly` |
| weekly-reviewer | Weekly review vs. goals | `/weekly` command |
| code-reviewer | Code quality review | After writing code |
| code-simplifier | Code clarity + maintainability | After modifying code |

## Parallel Dispatch (Default)

ALWAYS dispatch independent agents in parallel. Never sequential when parallel is possible:

```
GOOD: Launch calendar-briefer + email-triager + task-prioritizer simultaneously
BAD:  Run calendar-briefer, wait, then email-triager, wait, then task-prioritizer
```

## Orchestration Rules

1. Dispatch specialized agents for their domain — don't do everything in one context
2. Synthesize results into a single coherent output — don't just concatenate agent outputs
3. Use Haiku for lightweight classification/routing tasks; Sonnet for analysis; Opus for deep reasoning
4. If an agent fails or returns nothing useful, note it but don't block the overall output

## Multi-Perspective Analysis

For complex decisions or analysis, use split-role sub-agents:
- Strategic analyst (big picture, second-order effects)
- Devil's advocate (what could go wrong, weak points)
- Tactician (concrete next steps, what to do now)
