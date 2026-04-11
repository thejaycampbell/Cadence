---
name: morning
description: Daily morning brief. Dispatches parallel agents to pull calendar, email, and task context, then synthesizes into a 5-minute read. Run at the start of each day.
---

Generate my morning brief for today.

## How to run this

1. Read `context/ABOUT_ME.md` and `knowledge/00_user-brain/living-brain.md` for context on who I am and what I'm working toward.

2. Dispatch these 3 agents **in parallel**:

   **Agent 1 — calendar-briefer**
   Pull today's calendar. Summarize: what's on the schedule, when are back-to-backs, what needs prep time before it, what I should be thinking about.
   If Google Calendar MCP is not connected: skip and note it in output.

   **Agent 2 — email-triager**
   Triage my inbox. Return: what needs a response today, what's flagged urgent, what can wait, what can be ignored.
   If Gmail MCP is not connected: skip and note it in output.

   **Agent 3 — task-prioritizer**
   Review any outstanding items from `inbox/` and recent `meeting-notes/` entries. Score against today's goals from `living-brain.md`. Return top 3 things to move on today.

3. Synthesize all 3 outputs into a single morning brief. Format:

---

## Morning Brief — [Today's Date]

**Today's top 3:**
1. [Most important thing]
2. [Second]
3. [Third]

**Schedule:**
[Calendar summary — times, prep needed, back-to-backs]

**Inbox flags:**
[Priority email items — what needs action, by when]

**One decision to make today:**
[The most important unresolved question or choice based on context]

---

4. If 2+ MCPs are not connected, fall back to:
   - Read `living-brain.md` goals
   - Check `inbox/` for any unprocessed items
   - Generate a reflection prompt based on current goals
   - Ask: "What are the 3 most important things to move on today?"
