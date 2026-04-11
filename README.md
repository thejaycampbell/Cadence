# Cadence

A personal agentic operating system built on Claude Code.

Cadence turns Claude Code into a system that knows who you are, reasons through your frameworks, writes in your voice, handles your daily rituals, and gets sharper with every session.

**The article told you to build context files. Cadence is what comes after that.**

---

## What Cadence does

The article "I Don't Write Code. I Turned Claude Code Into My Personal Operating System" describes a system where you build text files that give Claude better context. That's a good start.

Cadence goes further:

- **Autonomous orchestrator** — slash commands dispatch specialized agents in parallel. `/morning` runs 3 agents simultaneously and synthesizes them into your daily brief.
- **Agent fleet** — 11 specialized agents, each expert in one domain. Calendar, email, research, writing, meeting prep, knowledge management.
- **Compounding knowledge graph** — every claim you capture compounds. Every decision has preserved rationale. Your past thinking shapes future analysis.
- **Daily ritual automation** — `/morning`, `/prep`, `/eod`, `/weekly`. Run them manually or schedule them.

The complexity is invisible. You type one command.

---

## Prerequisites

- [Claude Pro or Max subscription](https://claude.ai) ($20–$100/month)
- A GitHub account (free)
- [Claude Code](https://claude.ai/code) — available via Claude.ai desktop app or IDE extension

That's it. No backend server. No deployment. No Node.js required.

---

## Setup (30–60 minutes)

### 1. Create your repo from this template

Click **"Use this template"** at the top of this GitHub repo → **"Create a new repository"**

Give it a name (e.g., `my-cadence`), make it **private** (your context files will be personal), and create.

### 2. Clone and open in Claude Code

```bash
git clone https://github.com/[your-username]/[your-repo-name]
cd [your-repo-name]
```

Open Claude Code in this directory:
- **Desktop app**: File → Open → select the folder
- **IDE extension**: Open the folder, then open Claude Code in the integrated terminal

### 3. Run /onboard

In Claude Code, type:

```
/onboard
```

Claude will interview you for 30–60 minutes. By the end, it will know:
- Who you are and what you're working on
- How you think through problems
- How you write
- How you want to be challenged
- What you're trying to accomplish

Everything is personal. Nothing gets committed to GitHub (see `.gitignore`).

---

## Daily commands

Once onboarded, these are your tools:

| Command | What it does |
|---------|-------------|
| `/morning` | Daily brief — calendar + email + priorities, synthesized |
| `/prep [name or topic]` | Meeting prep — research + history before any call |
| `/research [topic]` | Parallel research brief — multiple angles, one output |
| `/write [type] [topic]` | Draft in your voice — research → outline → draft → voice check |
| `/eod` | End-of-day review — what got done, what's next |
| `/weekly` | Weekly review against your 90-day goals |
| `/meeting-notes` | Transcript → structured notes → updates INDEX and PEOPLE |
| `/add-claim [insight]` | Add an atomic insight to your knowledge graph |
| `/context-prime` | Load your full context at the start of any session |
| `/commit` | Stage and create a git commit from current changes |
| `/code-review [PR]` | Review a GitHub pull request via `gh` (requires auth) |
| `/capabilities` | Guided tour of all commands, agents, and bundled skills |

After `/onboard`, read **`CADENCE_CAPABILITIES.md`** once (or run **`/capabilities`**) for the full learning session on pre-built skills.

---

## Connecting integrations

Cadence works without integrations — it uses your knowledge base and context files.
With integrations, it can pull live calendar, email, and tool data.

### GitHub (pre-configured)

Create a personal access token at [github.com/settings/tokens](https://github.com/settings/tokens) with `repo` and `read:org` scopes. Set it as an environment variable:

```bash
# Add to ~/.bashrc or ~/.zshrc
export GITHUB_TOKEN=ghp_your_token_here
```

### Notion

1. Go to [notion.so/my-integrations](https://www.notion.so/my-integrations) → New Integration
2. Copy the Internal Integration Secret
3. Open `.claude/mcp-examples.md`, copy the **Notion** JSON block, and merge it into `"mcpServers"` in `.claude/settings.json` (valid JSON — add a comma between entries). Put your secret in `NOTION_API_KEY`.
4. Restart Claude Code

### Gmail + Google Calendar

OAuth setup required — about 20 minutes.

1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Create a project → Enable Gmail API + Google Calendar API
3. Create OAuth credentials (Desktop app type) → Download JSON
4. Follow the auth flow to generate a refresh token
5. Add credentials to `.claude/settings.json` (see the commented block)

### Slack

1. Go to [api.slack.com/apps](https://api.slack.com/apps) → Create New App
2. Add OAuth scopes: `channels:read`, `chat:write`, `im:read`
3. Install to workspace → copy Bot User OAuth Token
4. Copy the **Slack** block from `.claude/mcp-examples.md` into `"mcpServers"` in `.claude/settings.json` and set `SLACK_BOT_TOKEN`

---

## Enabling the autonomous morning brief (optional)

If you want a morning brief delivered to your email even when Claude Code isn't open:

1. Sign up at [resend.com](https://resend.com) (free tier works)
2. Get your Resend API key
3. Go to your GitHub repo → Settings → Secrets and variables → Actions
4. Add these secrets:
   - `ANTHROPIC_API_KEY` — from [console.anthropic.com](https://console.anthropic.com/settings/keys)
   - `RESEND_API_KEY` — from Resend dashboard
   - `BRIEF_TO_EMAIL` — your email address
5. Open `.github/workflows/morning-brief.yml` and uncomment the `schedule:` line
6. Push to GitHub

The brief runs automatically on weekdays at the time you set (default: 8am ET).

---

## How the knowledge graph works

Your `knowledge/` directory is the compounding brain.

**Core claims** (`knowledge/03_projects/core-claims.md`) are titled as declarative statements — specific, arguable, yours:

```
"Shipped features are not delivered value."
"Most SaaS companies confuse feature requests with customer focus."
```

This is different from category-based notes. Claim titles force precision. They're searchable by meaning. They compound over time.

Add to your knowledge graph with `/add-claim [insight]`. Claude checks for duplicates and contradictions before adding.

---

## File structure

```
CADENCE_CAPABILITIES.md  ← Reference: all slash commands, agents, and bundled skills.
context/           ← Read-only after /onboard. Who you are, how you think, your voice.
knowledge/         ← Your compounding brain. Add to it, never delete from it.
outputs/           ← Everything generated here. Versioned.
inbox/             ← Drop raw captures here for triage.
meeting-notes/     ← Searchable meeting archive.
memory/            ← Claude's session memory. Updated automatically.
.claude/           ← System configuration. Don't edit unless changing behavior.
```

**What gets committed to GitHub:** System configuration (`.claude/`), knowledge base (`knowledge/`), meeting notes, outputs.

**What never gets committed:** `context/` (personal identity files), `memory/` (session memory), `.env`, credential files. These are in `.gitignore`.

---

## Adding a new ritual

Power users can add custom commands:

1. Create a new file in `.claude/commands/` (e.g., `investor-update.md`)
2. Write the command following the same pattern as existing commands
3. Add any needed agents to `.claude/agents/`
4. Run `/onboard` again to configure scheduling if needed

---

## Built by

Cadence was built by [Jay Campbell](https://thejaycampbell.com).
