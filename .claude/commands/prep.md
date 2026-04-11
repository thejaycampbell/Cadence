---
name: prep
description: Meeting and call prep. Research a person, company, or topic before a conversation. Run as /prep [name or topic].
---

Prepare me for a meeting or call with: $ARGUMENTS

## How to run this

1. Read `context/ABOUT_ME.md` and `meeting-notes/PEOPLE.md` for relevant history and context.

2. Dispatch these 2 agents **in parallel**:

   **Agent 1 — meeting-prepper**
   Research: $ARGUMENTS
   Find out: who they are, what company/role, what they care about, recent news or activity, relevant background. Use web search and GitHub MCP if connected.

   **Agent 2 — knowledge-updater (read-only)**
   Search `meeting-notes/` and `knowledge/` for any prior context on this person, company, or topic. Return: what we know, what was decided, what was promised, any watchouts.

3. Synthesize into a prep brief:

---

## Prep Brief — [Name / Topic]

**Who they are:**
[Role, company, background — 2-3 sentences]

**What they care about:**
[Their priorities, current challenges, what they're trying to accomplish]

**Our history:**
[Prior conversations, decisions, commitments — from meeting-notes/ and knowledge/]

**Suggested questions:**
1. [Question based on their context and your goals]
2. [Question]
3. [Question]

**Watchouts:**
[Anything to be aware of — sensitivities, prior friction, open items]

**Your goal for this conversation:**
[Based on living-brain.md goals — what does a successful outcome look like?]

---

4. After generating the brief, ask: "Anything specific you want me to dig into before this call?"
