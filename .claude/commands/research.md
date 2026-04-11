---
name: research
description: Parallel research on any topic. Dispatches multiple research agents with different angles, synthesizes into one structured brief. Run as /research [topic].
---

Research: $ARGUMENTS

## How to run this

1. Read `context/ABOUT_ME.md` and `context/THINKING_MODELS.md` to understand how to frame the research for this user.

2. Determine the right research angles based on the topic. Default to 3 parallel angles:
   - **Market/landscape view** — What's the state of play? Who are the players? What are the dynamics?
   - **Competitive/comparative view** — How do alternatives compare? What are the tradeoffs?
   - **Evidence/ground-truth view** — What do customers, users, or practitioners actually say? What does the data show?

   Adapt angles based on topic type:
   - Strategy question → strategic + evidence + precedent
   - Person/company → background + recent activity + relationship to my goals
   - Technical topic → technical landscape + practical tradeoffs + adoption evidence

3. Dispatch 3 **researcher** agents in parallel, each with a different angle. Give each agent the topic and its specific angle.

4. Synthesize all 3 outputs into one research brief:

---

## Research Brief — [Topic]

**Bottom line up front:**
[1-2 sentence answer to the most important question the research surfaced]

**Landscape:**
[Key players, dynamics, state of the market/field]

**Tradeoffs / comparisons:**
[How options compare, what the real differences are]

**Ground truth:**
[What practitioners, users, or data actually show — not what vendors claim]

**What this means for me:**
[Implications given context/ABOUT_ME.md and living-brain.md goals]

**Gaps / follow-up questions:**
[What this research didn't answer — what to investigate next if needed]

---

5. Save the brief to `outputs/research_[topic-slug]_v1.md`
6. Ask: "Want me to go deeper on any angle?"
