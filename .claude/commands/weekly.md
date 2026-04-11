---
name: weekly
description: Weekly review against your 90-day goals. Surfaces patterns, updates your knowledge graph, and sets up next week.
---

Run my weekly review.

## How to run this

1. Read:
   - `knowledge/00_user-brain/living-brain.md` — 90-day goals and decision rules
   - `meeting-notes/INDEX.md` — this week's meetings
   - `knowledge/03_projects/core-claims.md` — current claims
   - `memory/MEMORY.md` — active project context

2. Dispatch 2 agents **in parallel**:

   **Agent 1 — weekly-reviewer**
   Analyze this week against the 90-day goals. What progress was made? What didn't move? What patterns emerged across meetings and work? What should be adjusted?

   **Agent 2 — knowledge-updater**
   Review this week's output: meeting notes, inbox items, any research or writing. Surface anything that should be added to the knowledge graph as a new claim or refinement.

3. Walk the user through:
   - "Here's what I see from this week. Does this match your read?"
   - "What did you learn this week that's worth keeping?"
   - "Anything in the knowledge base that needs updating?"

4. Based on their answers, update:
   - `knowledge/03_projects/core-claims.md` if new claims emerged
   - `knowledge/03_projects/decision-principles.md` if new principles crystallized
   - `memory/MEMORY.md` if project context changed

5. Return:

---

## Weekly Review — Week of [Date]

**Progress against 90-day goals:**
[For each goal: red/yellow/green + brief status]

**What moved:**
[Meaningful progress this week]

**What didn't move:**
[Stuck items — why, and what to do about it]

**Patterns from the week:**
[Recurring themes across meetings, decisions, or work]

**Knowledge updates:**
[New claims or principle updates added]

**Next week's top 3:**
1. [Most important thing for next week]
2.
3.

**One thing to kill or stop:**
[Based on this week's review — something to eliminate]

---
