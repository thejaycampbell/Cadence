---
name: capabilities
description: Full learning session on Cadence slash commands, agents, and bundled skills — what each does and how to use them. Reads CADENCE_CAPABILITIES.md and answers follow-up questions.
---

You are delivering the **Cadence capabilities tour** for a new (or returning) user.

## How to run this

1. Read `CADENCE_CAPABILITIES.md` at the repository root. If it is missing, say so and summarize from `.claude/commands/`, `.claude/agents/`, and `.claude/skills/` instead.

2. Give a **short spoken overview** (8–12 sentences) covering:
   - The three layers: slash commands → agents → skills
   - That skills live under `.claude/skills/<name>/SKILL.md` and load when tasks match their descriptions
   - The commands they will likely use weekly (`/morning`, `/prep`, `/research`, `/write`, `/eod`, `/weekly`, `/add-claim`, `/context-prime`)
   - That `/commit` and `/code-review` are for git/GitHub workflows when those tools are available

3. **Interactive pass:** Ask the user which area they care about most right now (e.g. daily rituals, writing, research, coding, fundraising). Deepen only that section:
   - Name the relevant slash commands and which agents they pull in
   - Point to 3–6 skill folders that match, with one sentence each from that skill’s `description` or intro

4. **Close** with: where the full tables live (`CADENCE_CAPABILITIES.md`), and that they can say *“use the `<skill-folder-name>` skill”* anytime.

Do not delete or edit user files unless they explicitly ask you to update context or knowledge.
