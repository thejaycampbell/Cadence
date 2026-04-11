---
name: weekly
description: Weekly review against your 90-day goals. Surfaces patterns, updates your knowledge graph, runs a maintenance diff on stale context, and sets up next week.
---

Run my weekly review.

## How to run this

1. Read:
   - `knowledge/00_user-brain/living-brain.md` — 90-day goals and decision rules
   - `knowledge/00_user-brain/icp-evolution.md` — ICP history (if it exists)
   - `meeting-notes/INDEX.md` — this week's meetings
   - `knowledge/03_projects/core-claims.md` — current claims with timestamps
   - `memory/MEMORY.md` — active project context
   - All files in `context/` — check for staleness

2. Dispatch 3 agents **in parallel**:

   **Agent 1 — weekly-reviewer**
   Analyze this week against the 90-day goals. What progress was made? What didn't move? What patterns emerged across meetings and work? What should be adjusted?

   **Agent 2 — knowledge-updater**
   Review this week's output: meeting notes, inbox items, any research or writing. Surface anything that should be added to the knowledge graph as a new claim or refinement.

   **Agent 3 — maintenance-checker** *(inline, no separate agent needed)*
   Scan for staleness across the entire system:
   - **Claims decay:** Find any claims in `core-claims.md` where `Added:` or `Validated:` is more than 60 days ago and `Status: active`. Flag each one: "This claim is [N] days old — still true?"
   - **Goals drift:** Search for any files matching `*goals*`, `*90-day*`, or `*priorities*` outside of `living-brain.md`. If found, compare to `living-brain.md` — flag any contradictions or duplication. Living-brain.md is the single source of truth.
   - **Context staleness:** Check `context/` files. If any section of ABOUT_ME, THINKING_MODELS, VOICE_CALIBRATION, or WORKING_PREFERENCES references a role, project, or tool you no longer use, flag it.
   - **ICP check:** Does anything from this week's meetings suggest the ICP definition needs updating? If yes, draft the new entry for `icp-evolution.md`.

3. Walk the user through the review output, then the maintenance diff:

   **Review:**
   - "Here's what I see from this week. Does this match your read?"
   - "What did you learn this week that's worth keeping?"
   - "Anything in the knowledge base that needs updating?"

   **Maintenance diff** (present as a numbered list of proposed changes):
   > "Here's what I found that may be stale. For each one, say yes to update, no to skip, or give me the correction:"
   >
   > 1. Claim: "[claim text]" — added [date], [N] days old. Still accurate?
   > 2. Goals drift: found [filename] with goals that differ from living-brain.md. Merge?
   > 3. Context: [specific section] references [thing] — is this still current?
   > 4. ICP: based on this week, [proposed update]. Add to icp-evolution.md?

   Wait for confirmation before making any changes.

4. Based on confirmed answers, update:
   - `knowledge/03_projects/core-claims.md` — new claims, updated `Validated:` dates, or retired status
   - `knowledge/03_projects/decision-principles.md` — new principles
   - `knowledge/00_user-brain/icp-evolution.md` — new ICP entry if ICP shifted
   - `knowledge/00_user-brain/living-brain.md` — goal updates
   - `context/` files — any confirmed staleness corrections
   - `memory/MEMORY.md` — updated project context
   - Merge or delete any duplicate goal files found

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

**Maintenance changes made:**
[List of stale items confirmed and updated — or "nothing stale this week"]

**Next week's top 3:**
1. [Most important thing for next week]
2.
3.

**One thing to kill or stop:**
[Based on this week's review — something to eliminate]

---
