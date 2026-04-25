[![RepoRanker](https://reporanker.com/badge/thejaycampbell/Cadence)](https://reporanker.com/repos/thejaycampbell/Cadence)
# Cadence

A personal agentic operating system built on Claude Code.

Cadence turns Claude Code into a system that knows who you are, reasons through your frameworks, writes in your voice, handles your daily rituals, and gets sharper with every session.

Loose context files are not enough on their own. Cadence adds **structure**: a defined identity layer, repeatable slash commands, parallel agents, and a compounding knowledge graph—so your context becomes a system you run every day, not a folder you forget.

---

## What Cadence does

- **Orchestrated commands** — Slash commands dispatch specialized agents in parallel. `/morning` runs three agents and synthesizes them into one daily brief.
- **Agent fleet** — Eleven agents, each scoped to one job: calendar, email, research, writing, meeting prep, knowledge updates, and more.
- **Compounding knowledge graph** — Claims and principles live in `knowledge/` and accumulate; past reasoning informs the next analysis.
- **Daily rituals** — `/morning`, `/prep`, `/eod`, `/weekly`. Run on demand or wire automation (see below).

The complexity stays in the repo. In the chat, you usually type one command.

---

## Prerequisites

- [Claude Pro or Max subscription](https://claude.ai) ($20–$100/month)
- A GitHub account (free)
- [Claude Code](https://claude.ai/code) — Claude.ai desktop app or IDE extension

No backend server, no deployment, and no Node.js required for the core experience.

---

## Setup (30–60 minutes)

### 1. Create your repo from this template

Click **Use this template** on this GitHub repo → **Create a new repository**.

Name it (e.g. `my-cadence`), keep it **private** if your context will be personal, and create.

### 2. Clone and open in Claude Code

```bash
git clone https://github.com/[your-username]/[your-repo-name]
cd [your-repo-name]
```

Open this folder in Claude Code:

- **Desktop app:** File → Open → select the folder  
- **IDE extension:** Open the folder, then open Claude Code from the integrated terminal

### 3. Run `/onboard`

In Claude Code:

```
/onboard
```

Claude interviews you for roughly 30–60 minutes. When you finish, it has populated:

- Who you are and what you are working on  
- How you think and decide  
- How you write and how you want to be challenged  
- What you are trying to accomplish  

Personal files under `context/` and `memory/` stay local (see `.gitignore`).

---

## Commands

After onboarding, these are the main entry points:

| Command | What it does |
|---------|----------------|
| `/morning` | Daily brief — calendar + email + priorities, synthesized |
| `/prep [name or topic]` | Meeting prep — research + history before a call |
| `/research [topic]` | Parallel research brief — multiple angles, one output |
| `/write [type] [topic]` | Draft in your voice — research → outline → draft → voice check |
| `/eod` | End-of-day review — what got done, what is next |
| `/weekly` | Weekly review against your 90-day goals |
| `/meeting-notes` | Transcript → structured notes; updates meeting archive |
| `/add-claim [insight]` | Add an atomic insight to your knowledge graph |
| `/context-prime` | Reload full personal context at the start of a session |
| `/commit` | Stage and create a git commit from current changes |
| `/code-review [PR]` | Review a GitHub pull request via `gh` (requires auth) |
| `/capabilities` | Guided tour of commands, agents, and bundled skills |

Read **`CADENCE_CAPABILITIES.md`** once, or run **`/capabilities`**, for the full map of commands, agents, and **67** bundled skills under `.claude/skills/`.

---

## Connecting integrations

Cadence works without integrations using your markdown knowledge and context.

With MCPs connected, commands can pull live calendar, email, and other tool data.

### GitHub (pre-configured in `.claude/settings.json`)

Create a personal access token at [github.com/settings/tokens](https://github.com/settings/tokens) with `repo` and `read:org` scopes:

```bash
# Add to your shell profile
export GITHUB_TOKEN=ghp_your_token_here
```

### Notion

1. [notion.so/my-integrations](https://www.notion.so/my-integrations) → New integration → copy the Internal Integration Secret  
2. Copy the **Notion** block from `.claude/mcp-examples.md` into `"mcpServers"` in `.claude/settings.json` (valid JSON; comma between entries). Set `NOTION_API_KEY`.  
3. Restart Claude Code  

### Gmail + Google Calendar

OAuth setup (~20 minutes):

1. [console.cloud.google.com](https://console.cloud.google.com) → new project → enable Gmail API and Google Calendar API  
2. OAuth credentials (Desktop app) → download JSON  
3. Complete the auth flow for a refresh token  
4. Merge the **Google** block from `.claude/mcp-examples.md` into `.claude/settings.json`  

### Slack

1. [api.slack.com/apps](https://api.slack.com/apps) → Create New App  
2. Scopes: `channels:read`, `chat:write`, `im:read`  
3. Install to workspace → copy Bot User OAuth Token  
4. Copy the **Slack** block from `.claude/mcp-examples.md` into `.claude/settings.json` and set `SLACK_BOT_TOKEN`  

---

## Autonomous morning brief (optional)

To receive a morning brief by email when Claude Code is not open:

1. [resend.com](https://resend.com) — create an API key  
2. Repo → **Settings** → **Secrets and variables** → **Actions** — add:  
   - `ANTHROPIC_API_KEY` — [console.anthropic.com](https://console.anthropic.com/settings/keys)  
   - `RESEND_API_KEY`  
   - `BRIEF_TO_EMAIL`  
3. In `.github/workflows/morning-brief.yml`, uncomment the `schedule:` line  
4. Push to GitHub  

Default schedule: weekdays, 8am ET (adjust in the workflow).

---

## Knowledge graph

`knowledge/` is the long-lived brain.

**Core claims** in `knowledge/03_projects/core-claims.md` are declarative statements—specific, arguable, yours:

```
"Shipped features are not delivered value."
"Most SaaS companies confuse feature requests with customer focus."
```

Claim-style notes stay searchable and compound over time. Add with `/add-claim [insight]`; Claude can help deduplicate and surface tensions.

---

## File structure

```
CADENCE_CAPABILITIES.md   ← Commands, agents, and bundled skills
context/                  ← Identity, thinking models, voice (after /onboard)
knowledge/                ← Claims, principles, style guides
outputs/                  ← Generated artifacts
outputs/dashboards/       ← Static HTML hub, goals, claims boards
inbox/                    ← Raw captures for triage
meeting-notes/            ← Meeting archive
memory/                   ← Session routing and profile pointers
.claude/                  ← Commands, agents, rules, skills, settings
```

**Typically committed:** `.claude/`, `knowledge/`, `meeting-notes/`, `outputs/`, and other non-ignored project files.

**Ignored by default:** `context/`, `memory/`, `.env`, credential files (see `.gitignore`).

---

## Custom rituals

1. Add a file in `.claude/commands/` (follow existing frontmatter and body pattern).  
2. Add agents under `.claude/agents/` if you need new behavior.  
3. Use `/onboard` again if you want to document scheduling or preferences.  

---

## Static dashboards

Open **`outputs/dashboards/cadence-hub.html`** in a browser for a local home screen; **`goals-scorecard.html`** and **`claims-board.html`** mirror goals and claims. See **`outputs/dashboards/README.md`**.

---

## Built by

Cadence was built by [Jay Campbell](https://thejaycampbell.com).
