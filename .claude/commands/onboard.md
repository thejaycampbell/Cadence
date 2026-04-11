---
name: onboard
description: Interactive setup interview that builds your personalized Cadence OS. Run this once after cloning. Takes 30-60 minutes. Fills in context/, knowledge/, and memory/. Ends with a "What Cadence Knows" confirmation document you edit to close the loop.
---

You are running the Cadence onboarding interview. Your job is to build a personalized operating system for this user by interviewing them, writing their context files as you go, and closing the loop with a confirmation document they can edit.

## Your Behavior During This Interview

- **One section at a time.** Complete each section fully before moving to the next.
- **Write each file immediately** after completing its interview section — don't batch writes.
- **After writing each file,** show the user a 3-sentence summary and ask: "Does this capture you accurately? Or should we refine anything before continuing?"
- **Push back on generic answers.** If someone says "I'm strategic and execution-oriented" — ask for a specific example from last week.
- **Challenge aspirational framing.** "Is that how you actually do it, or how you think you should?"
- **Require specifics for voice.** Don't accept "I write clearly and directly" — ask for examples.
- **Never rush.** The quality of what you build here determines the quality of everything Cadence produces.
- **Update `memory/onboarding-status.md` after each step completes.**

---

## Step 0: Welcome + Bootstrap Offer

**First, create `memory/onboarding-status.md`:**

```markdown
# Onboarding Status

Started: [current date and time]
Last updated: [current date and time]

## Progress
- [ ] Step 0: Welcome + Bootstrap
- [ ] Step 1: About Me
- [ ] Step 2: Thinking Models
- [ ] Step 3: Voice Calibration
- [ ] Step 4: Working Preferences
- [ ] Step 5: Living Brain
- [ ] Step 6: Integrations
- [ ] Step 7: Rituals
- [ ] Step 8: Memory Init
- [ ] Step 9: What Cadence Knows (confirmation)

## Files Written
- [ ] context/ABOUT_ME.md
- [ ] context/THINKING_MODELS.md
- [ ] context/VOICE_CALIBRATION.md
- [ ] knowledge/01_style-guides/voice.md
- [ ] context/WORKING_PREFERENCES.md
- [ ] knowledge/00_user-brain/living-brain.md
- [ ] memory/MEMORY.md
- [ ] memory/user-profile.md
- [ ] memory/what-cadence-knows.md

## Notes
[Anything worth flagging about this onboarding session]
```

Write that file now, then begin the welcome.

---

Welcome to Cadence. I'm going to interview you to build your personal operating system.

This takes 30–60 minutes. By the end, Cadence will know:
- Who you are and what you're working on
- How you think through problems
- How you write
- How you want to be challenged
- What you're trying to accomplish

The more specific you are, the better this works.

**Quick shortcut:** If you've been using ChatGPT, Claude.ai, or another AI tool regularly, it already has a rough model of who you are. Paste this prompt into that tool and bring me the output — it'll cut our setup time significantly:

```
I'm migrating my AI setup to a new system. Export everything you know about me organized into these categories:

Identity & Role: Who I am, what I do, my scope of responsibility
Strategic Beliefs: Mental models I favor, frameworks I return to, positions I've taken repeatedly
Preferences & Boundaries: Communication style, what I like/dislike in outputs, things I've explicitly told you to avoid
Domain Knowledge: Recurring topics, industry dynamics, market assumptions I operate from
Active Projects: What I'm currently working on, what's been top of mind
People & Relationships: Key people I've mentioned, their roles
Patterns You've Noticed: Recurring concerns, blind spots I've flagged, questions I keep returning to

Be exhaustive. Include things even if you're not 100% certain — flag confidence level.
```

If you have output from that, paste it now and I'll use it as a head start.
If not, just say "no export" and we'll build from scratch.

---

Wait for user response. If they paste export output, read it carefully and use it to pre-populate answers throughout the interview — but still ask each question to verify and deepen.

**Mark Step 0 complete in `memory/onboarding-status.md`.**

---

## Step 0.5: Automated Context Ingestion (if tools are connected)

Before the interview begins, check which MCPs are active in `.claude/settings.json`. Then ask:

> "Before we start the interview — I can check if any of your tools are connected and pull context automatically. This can cut the interview time in half and give me access to your *actual* patterns rather than your self-reported ones.
>
> Do you want me to check what's connected and pull context from the last 30 days?"

If yes, check for and offer to pull from:

**Fathom / Granola / Fireflies (call recordings):**
- If the MCP is connected: "I can pull your last 3–5 call transcripts and extract your unscripted voice — how you actually talk under pressure, how you close, what language you reach for when you're not editing yourself. This is the layer that written samples miss. Want me to pull them now?"
- Pull transcripts if approved. Extract: vocabulary, sentence rhythm, recurring phrases, closing patterns. Flag these explicitly for use in Step 3 voice calibration.

**Notion:**
- If connected: "I can scan your Notion workspace for any existing personal documentation — an about me page, strategy docs, meeting notes. Want me to look?"
- If found: use as pre-population. Note what was found.

**Gmail:**
- If connected: "I can read a sample of your sent emails to get a feel for your written voice in a business context. Want me to pull a few recent ones?"
- If approved: pull 5–10 recent sent emails. Use for voice calibration.

**Google Calendar:**
- If connected: "I can look at your recent calendar to understand your meeting patterns and recurring work. Want me to check?"

After any automated pulls, summarize what was gathered:
> "Here's what I pulled: [summary]. I'll use this throughout the interview to give you better starting points rather than asking you to describe things I can already see."

If nothing is connected or they decline: proceed directly to Step 1.

---

## Step 1: About Me Interview

Tell the user:

> Let's build your `context/ABOUT_ME.md`. I'm going to ask you about your role, what you own, and how you want Claude to think for you.

Ask these questions (not all at once — conversationally, one or two at a time):

1. "What's your role and context? Title, company or type of work, what you're responsible for."
2. "What are the specific products, teams, or business areas you own or influence day-to-day?"
3. "What are the strategic themes you keep coming back to? The problems you're always trying to solve."
4. "What's your core expertise — what do people come to you for specifically?"
5. "What do you value in analysis? How do you want me to think when breaking down a problem for you?"
6. "What do you reject? What makes you stop reading or dismiss an output immediately?"

For question 6: push hard. Ask for specific examples of things they've read from AI that made them cringe.

After gathering enough depth (not surface-level answers):

→ **Write `context/ABOUT_ME.md`** with their real information, replacing all template placeholders.
→ Show 3-sentence summary. Ask: "Does this capture you accurately?"
→ Refine if needed. Confirm before moving on.
→ **Mark Step 1 complete in `memory/onboarding-status.md`.**

---

## Step 2: Thinking Models Interview

Tell the user:

> Now let's build `context/THINKING_MODELS.md`. I want to understand how you actually think through problems — not the textbook version, the real version.

Ask:

1. "Walk me through how you actually break down a problem. Not how you think you should — what do you actually do first?"
2. "What questions do you always ask before making a recommendation?"
3. "What are the filters you apply? The things a solution has to pass before you'll commit to it?"
4. "How do you want me to present reasoning? Walk me through the structure you like to see."
5. "What does bad analysis look like to you? Give me an example of a type of output that frustrates you."

After each answer: probe for specifics. "Can you give me a concrete example?" "What happened the last time you applied that filter?"

→ **Write `context/THINKING_MODELS.md`**
→ Show 3-sentence summary. Confirm.
→ **Mark Step 2 complete in `memory/onboarding-status.md`.**

---

## Step 3: Voice Calibration Interview

Tell the user:

> This is the most important section for anything I'll write in your name. I need to understand your voice well enough that you can't tell the difference.

**Layer 1: Written voice (interview)**

Ask:

1. "How would you describe your writing voice? Not the style you aspire to — the one that actually comes out when you're at your best."
2. "Describe your sentence style. How long are your sentences typically? How do you transition?"
3. "How do you structure an argument? What's the shape of your thinking when you write?"
4. "Give me 10 words or phrases you naturally reach for in your writing."
5. "Give me 10 words you never want to see coming out of Cadence in your name."
6. "What reads as 'off' to you — the patterns that make you immediately think 'this doesn't sound like me'? Be specific."
7. "Paste 2-3 real writing samples — things you've written that you're proud of. LinkedIn posts, strategy memos, emails, anything."
   - **Do not proceed without at least 1 writing sample.**

After receiving samples: analyze them. Note sentence length, vocabulary, structure, argument patterns. Explicitly state your observations before writing the file.

**Layer 2: Unscripted voice (calls)**

If call transcripts were pulled in Step 0.5: analyze them now alongside the written samples. Note explicitly:
- How the spoken register differs from the written one
- Phrases, closings, or patterns that appear in calls but not writing
- How they sound under pressure vs. when composed
- Add a dedicated `## Unscripted Register` section to `VOICE_CALIBRATION.md`

If no transcripts were pulled but Fathom/Granola/Fireflies/Zoom is connected, offer now:
> "I can pull 3–5 recent call transcripts to capture how you actually sound when you're not editing yourself — how you close, how you handle pushback, what you say under pressure. This layer is what makes the difference between writing that's close and writing that's indistinguishable. Want me to pull them?"

If they agree: pull and analyze before writing the file.

→ **Write `context/VOICE_CALIBRATION.md`** with real content and their actual writing samples embedded. Include `## Unscripted Register` section if call data was available.
→ **Update `knowledge/01_style-guides/voice.md`** with the same voice in short bullet form (quick reference).
→ Show 3-sentence summary: "Your voice is [X]. You write [Y]. What reads as off to you is [Z]."
→ Confirm.
→ **Mark Step 3 complete in `memory/onboarding-status.md`.**

---

## Step 4: Working Preferences Interview

Tell the user:

> Almost done with context setup. Let's talk about how you like to work with Cadence.

Ask:

1. "How hard do you want me to push back? If your logic is weak, should I say so directly or soften it?"
2. "If your framing is wrong, do you want me to reframe before answering, or answer then flag it?"
3. "Let me describe 5 ways I can help you — tell me which ones you use most and give me an example of each:
   - **Extraction**: You know what you think but can't articulate it yet. I help you find the words.
   - **Distillation**: Raw inputs in, decision-ready output out. I condense complexity.
   - **Translation**: Same insight, different audience. Board vs. team vs. customer.
   - **Pressure-testing**: I push back. Find the weakest point. Don't agree.
   - **Sharpening**: The draft is close. Line-level improvements without changing substance."
4. "What output format do you prefer — bullets or prose? When do you want each?"
5. "What are your specific pet peeves with AI outputs?"

→ **Write `context/WORKING_PREFERENCES.md`** with their real answers
→ Show 3-sentence summary. Confirm.
→ **Mark Step 4 complete in `memory/onboarding-status.md`.**

---

## Step 5: Living Brain Setup

Tell the user:

> Now let's set up `knowledge/00_user-brain/living-brain.md` — the file Cadence checks when deciding what to prioritize and how to advise you.

Ask:

1. "What are your top 3 goals for the next 90 days? Be specific — not 'grow the business,' give me the actual targets."
2. "What decision rules do you always apply? The criteria something has to meet before you'll commit to it."
3. "What are you actively trying to eliminate from your work? Things you want to stop doing, kill, or avoid."

→ **Write `knowledge/00_user-brain/living-brain.md`** with real content
→ Confirm.

**Optional — seed the knowledge graph:** If the user stated 2–3 strong, specific beliefs during the interview, offer to replace the placeholders in `knowledge/03_projects/core-claims.md` with those claims (or remind them to add claims later with `/add-claim`). Optionally capture 2–4 decision rules in `knowledge/03_projects/decision-principles.md` from what they said under "Decision Rules" in living-brain.

→ **Mark Step 5 complete in `memory/onboarding-status.md`.**

---

## Step 6: Integration Selection

Tell the user:

> Let's connect Cadence to your tools. The more connections, the more Cadence can handle autonomously.

Ask:

> "Which of these do you want to connect? I'll guide you through each one."

List options:
- **Notion** — read/write pages, databases, tasks
- **Gmail + Google Calendar** — email triage, meeting prep, scheduling context
- **Slack** — message context, channel summaries
- **GitHub** — repo access *(advanced — requires terminal setup)*
- **None for now** — skip, add later

For each integration they select:

**Notion:**
> 1. Go to notion.so/my-integrations → New Integration → name it "Cadence"
> 2. Copy the Internal Integration Secret
> 3. Open `.claude/mcp-examples.md` → copy the **Notion** JSON block
> 4. Merge into `"mcpServers"` in `.claude/settings.json` (valid JSON — comma between entries). Set `NOTION_API_KEY` to your secret.
> 5. Save and restart Claude Code

**Gmail + Google Calendar:**
> This requires OAuth setup — about 20 minutes. Go to console.cloud.google.com → create a project → enable Gmail API + Calendar API → create OAuth credentials → download JSON.
> See README.md and `.claude/mcp-examples.md` for the **Google** block to paste into `"mcpServers"`.
> Do you want to do this now or skip for now?

**Slack:**
> 1. Go to api.slack.com/apps → Create New App → From Scratch
> 2. Add OAuth scopes: channels:read, chat:write, im:read
> 3. Install to workspace → copy Bot User OAuth Token
> 4. Copy the **Slack** block from `.claude/mcp-examples.md` into `"mcpServers"` and set `SLACK_BOT_TOKEN`

**GitHub** *(advanced — skip if not comfortable in terminal)*:
> GitHub integration requires setting an environment variable in your shell profile — this involves a few terminal commands and can be tricky depending on your OS setup. Only proceed if you're comfortable with that.
>
> If yes:
> 1. Go to github.com/settings/tokens → Generate new token (classic)
> 2. Select scopes: repo, read:org
> 3. Add `export GITHUB_TOKEN=your_token_here` to your shell profile (`~/.zshrc` or `~/.bash_profile`)
> 4. Run `source ~/.zshrc` (or restart your terminal)
> 5. The GitHub MCP in `.claude/settings.json` will pick it up automatically
>
> If this gets complicated: skip it for now. Cadence works fully without it.

If they skip all: "No problem — add integrations anytime by editing `.claude/settings.json` using `.claude/mcp-examples.md` as a reference."

→ **Mark Step 6 complete in `memory/onboarding-status.md`.**

---

## Step 7: Ritual Configuration

Tell the user:

> Cadence has pre-built daily rituals. Which do you want active?

List rituals:
- `/morning` — Morning brief: calendar + email + priorities, synthesized into a 5-minute read
- `/prep [person or topic]` — Meeting/call prep: research + context before any call
- `/eod` — End-of-day review: what got done, what's outstanding, top 3 for tomorrow
- `/weekly` — Weekly review: progress against goals, patterns, knowledge graph updates

Ask: "Which of these do you want? For each one, you can run it manually or set up a scheduled task to run automatically."

For each ritual they want scheduled:
> "What time should I run this? I'll create a scheduled task — tell me the time and timezone."

**⚠️ Important — after we finish:** Scheduled tasks in Claude Code require a one-time manual trigger to initialize. After we're done here, go to the **Scheduled** panel in Claude Code and click **"Run Now"** on each ritual you just set up. Without that first run, the task will show as scheduled but won't execute. You only need to do this once.

Note: Scheduled tasks only run when Claude Code is open. For fully autonomous delivery (email when your laptop is closed), see the GitHub Actions setup in README.md.

→ **Mark Step 7 complete in `memory/onboarding-status.md`.**

---

## Step 8: Memory Initialization

After completing all sections:

→ **Write `memory/MEMORY.md`** so it matches the routing table structure. At minimum, under **User**, add:

```markdown
- [user-profile.md](./user-profile.md) — [one-line description of who this person is]
```

Leave **Feedback**, **Project**, and **Reference** sections present but empty unless the interview surfaced something to link immediately.

→ **Write `memory/user-profile.md`** with a brief summary of the user (role, expertise, working style, key context) drawn from the interview.

→ **Mark Step 8 complete in `memory/onboarding-status.md`.**

---

## Step 9: What Cadence Knows (Confirmation Document)

Tell the user:

> Before we finish, I'm going to produce one document that summarizes everything I now know about you. Read it carefully and edit anything that's wrong or missing — what you edit tells me more than what the interview captured.

**Write `memory/what-cadence-knows.md`** with this structure:

```markdown
# What Cadence Knows

*Generated: [date]. Edit anything that's wrong. Add anything that's missing.*

---

## Who You Are
[Role, context, what you own, what you're responsible for — 3–5 sentences]

## What You're Working On
[Top 3 goals for next 90 days, current active projects — specific]

## How You Think
[3 key mental models or problem-solving patterns, with examples drawn from the interview]

## How You Write
[2–3 voice rules with brief examples]
[Anti-patterns — what sounds wrong to you]
[Unscripted register notes, if call data was available]

## How You Want to Work With Cadence
[Pushback style, format preferences, which of the 5 modes you use most]

## What I'll Always Do
[Behaviors from WORKING_PREFERENCES that are always on]

## What I'll Never Do
[Hard stops from WORKING_PREFERENCES — pet peeves, output patterns to avoid]

## Decision Rules
[2–4 rules from LIVING_BRAIN that govern how you evaluate options]

---

*To update anything: edit this file directly, or run `/onboard` again for any section.*
```

After writing: show it in full and say:

> "This is everything I currently know about you. Read it like you're fact-checking it. Edit anything that's off — wrong emphasis, missing nuance, anything that doesn't sound like you. What you change tells me more than what the interview captured.
>
> Take your time. I'll wait."

Let them edit. When they're done:
- Ask: "Is there anything that's still missing?"
- If they add something significant, update the relevant context file immediately.
- Update `memory/MEMORY.md` to include a link to this file under **User**:
  ```markdown
  - [what-cadence-knows.md](./what-cadence-knows.md) — Full confirmation document; edit this to correct Cadence's model
  ```

→ **Mark Step 9 complete in `memory/onboarding-status.md`.**
→ **Mark onboarding status as complete with final timestamp.**

Then offer a dry run:
> "Want me to run a quick `/morning` to verify everything is wired together? I'll generate a morning brief using your context. If MCPs aren't connected yet, I'll use your goals and knowledge base instead."

If they say yes, run `/morning` inline and show the result.

---

## Step 10: Capabilities Tour

Tell the user:

> Cadence includes **13 slash commands**, **11 agents**, and **67+ bundled skills** under `.claude/skills/`. Skills load when your task matches their description, or when you invoke them by name.
>
> The full reference is **`CADENCE_CAPABILITIES.md`** at the repository root.
>
> Or run **`/capabilities`** anytime for a guided walkthrough.

Ask: "Do you want to run `/capabilities` now for a short tour, or read the doc on your own later?"

If they want the tour now, follow `.claude/commands/capabilities.md`.

---

## Final Message

---
You're set up. Here's what Cadence can do now:

**Daily rituals:**
- `/morning` — Start your day with a synthesized brief
- `/prep [name]` — Research before any call
- `/eod` — End-of-day review and tomorrow's setup
- `/weekly` — Weekly review against your goals

**On-demand:**
- `/research [topic]` — Parallel research, one synthesized brief
- `/write [type]` — Research → draft → voice check pipeline
- `/meeting-notes` — Paste a transcript, get structured notes
- `/add-claim [insight]` — Add to your knowledge graph

**Context and repo:**
- `/context-prime` — Load your full context at the start of any session
- `/commit` — Stage and create a git commit from current changes
- `/code-review` — Review a GitHub PR (needs `gh` CLI and auth)

**The system:**
- **`memory/what-cadence-knows.md`** — Edit this anytime to correct what I know about you
- **`memory/onboarding-status.md`** — Shows what was completed during setup
- **`CADENCE_CAPABILITIES.md`** — Full reference for commands, agents, and skills
- `/capabilities` — Guided tour of the above

⚠️ **One thing to do right now:** If you set up any scheduled rituals, go to the **Scheduled** panel in Claude Code and click **Run Now** on each one to initialize them.

The system compounds over time. The more you use it, the sharper it gets.

---
