# Cadence capabilities — full reference

This document is the **learning tour** for everything shipped in this repo: slash commands, agents, and bundled **skills** (folders under `.claude/skills/`, each with a `SKILL.md`).

**How the pieces fit together**

| Layer | Location | What it is |
|-------|----------|------------|
| **Slash commands** | `.claude/commands/*.md` | What you type after `/` in Claude Code (e.g. `/morning`). Each file is a prompt recipe. |
| **Agents** | `.claude/agents/*.md` | Specialized sub-personas with a narrow job. Commands **dispatch** agents (often in parallel). |
| **Skills** | `.claude/skills/<name>/SKILL.md` | Deep playbooks on a topic. Claude Code can load a skill when your task matches its `description` in the YAML frontmatter. |

**How to use skills**

- **Implicitly:** Describe what you are doing in natural language. If it matches a skill’s description, the assistant should read that skill’s `SKILL.md` and follow it.
- **Explicitly:** Say *“Use the `<skill-folder-name>` skill”* or *“Follow `.claude/skills/<name>/SKILL.md`.”*
- **Discovery:** Every skill lives under `.claude/skills/<name>/`. Open any `SKILL.md` for the full workflow.

**Bundled plugins** (see `.claude/settings.json`)

- `superpowers@claude-plugins-official` — meta-workflows (planning, verification, subagents) aligned with many skills below.
- `claude-mem@thedotmack` — optional memory plugin for Claude Code.

---

## Slash commands (13)

| Command | What it does |
|---------|----------------|
| `/onboard` | Interactive interview; fills `context/`, seeds `knowledge/` and `memory/`. Run once after clone, or to refresh. |
| `/morning` | Parallel **calendar-briefer**, **email-triager**, **task-prioritizer** → one morning brief. |
| `/prep [person or topic]` | **meeting-prepper** — research + history before a call. |
| `/research [topic]` | **researcher** — multi-angle research brief. |
| `/write [type] [topic]` | **writer** — research → outline → draft → voice check. |
| `/eod` | End-of-day review and carry-over. |
| `/weekly` | **weekly-reviewer** — review vs 90-day goals and knowledge graph. |
| `/meeting-notes` | Transcript → structured notes; updates `meeting-notes/` and may prompt for knowledge captures. |
| `/add-claim [insight]` | Append a claim to `knowledge/03_projects/core-claims.md` with dedup checks. |
| `/context-prime` | Reload full personal context at session start. |
| `/commit` | Stage and create a git commit from current changes (uses git bash tools). |
| `/code-review [PR]` | PR review via `gh` CLI (requires GitHub auth). |
| `/capabilities` | Walk through this document (or answer questions about commands, agents, skills). |

---

## Agents (11)

| Agent | What it does | Used by |
|-------|----------------|---------|
| `morning-orchestrator` | Runs calendar + email + task agents in parallel; synthesizes one brief. | `/morning` |
| `calendar-briefer` | Day summary from calendar MCP (graceful if disconnected). | `morning-orchestrator`, `/prep` flows |
| `email-triager` | Prioritized inbox digest from Gmail MCP (graceful if disconnected). | `morning-orchestrator` |
| `task-prioritizer` | Scores `inbox/` + `meeting-notes/` vs goals in `living-brain.md`. | `/morning`, `/eod` |
| `meeting-prepper` | Person/company/topic research for calls. | `/prep` |
| `researcher` | One structured research angle (often 2–3 instances in parallel). | `/research` |
| `writer` | Drafts in your voice using `VOICE_CALIBRATION.md`. | `/write` |
| `weekly-reviewer` | Weekly review vs 90-day goals and patterns. | `/weekly` |
| `knowledge-updater` | Proposes updates to `core-claims.md` and `decision-principles.md` from the week’s material. | `/weekly` |
| `code-reviewer` | Guideline and style review before commit/PR. | After code changes (per agent doc) |
| `code-simplifier` | Simplify recent edits without changing behavior. | After coding tasks (per agent doc) |

Wiring details live in each file under `.claude/commands/` and `.claude/agents/`.

---

## Skills catalog (67)

Each row is a folder under `.claude/skills/`. Descriptions come from each `SKILL.md` frontmatter (or the intro where no YAML name/description exists).

### Planning, execution, and meta-workflow

| Skill folder | What it’s for |
|--------------|----------------|
| `brainstorming` | Explore intent and design **before** implementation (required for creative work in that workflow). |
| `writing-plans` | Multi-step task from spec — plan before code. |
| `executing-plans` | Run a written plan in a separate session with checkpoints. |
| `subagent-driven-development` | Execute plans with subagents in the current session. |
| `dispatching-parallel-agents` | Two or more independent tasks without shared state. |
| `finishing-a-development-branch` | Merge vs PR vs cleanup after work is done. |
| `strategic-compact` | When to compact context manually across phases. |
| `using-superpowers` | How to find and invoke skills at conversation start. |
| `verification-before-completion` | Run verification commands before claiming “done.” |
| `verification-loop` | Session-wide verification habits. |
| `eval-harness` | Eval-driven development for Claude Code sessions. |
| `dmux-workflows` | Multi-agent orchestration with dmux / tmux-style panes. |
| `everything-claude-code` | Conventions for the everything-claude-code JS project (narrow scope). |

### Product: PRDs, capabilities, refactors

| Skill folder | What it’s for |
|--------------|----------------|
| `write-a-prd` | Interview + codebase exploration → PRD as GitHub issue. |
| `prd-to-plan` | PRD → phased implementation plan (tracer bullets) in `./plans/`. |
| `prd-to-issues` | PRD → vertical-slice GitHub issues (see folder; intro describes flow). |
| `product-capability` | PRD/roadmap talk → implementation-ready capability spec. |
| `request-refactor-plan` | Refactor plan as small commits + GitHub issue. |
| `grill-me` | Stress-test a plan or design via structured Q&A. |
| `improve-codebase-architecture` | Explore codebase, surface friction, propose deep-module refactors (see `SKILL.md` intro). |
| `design-an-interface` | “Design it twice” — multiple designs, compare (see `SKILL.md` intro). |
| `ubiquitous-language` | DDD-style glossary from conversation → `UBIQUITOUS_LANGUAGE.md`. |
| `agent-sort` | Trim ECC-style bundles to “daily vs library” skills for a repo. |

### Engineering: code, tests, APIs, infra

| Skill folder | What it’s for |
|--------------|----------------|
| `api-design` | REST APIs: resources, errors, pagination, versioning. |
| `backend-patterns` | Node/Express/Next API routes, server patterns. |
| `coding-standards` | Cross-cutting code quality conventions. |
| `frontend-patterns` | React/Next state, performance, UI patterns. |
| `frontend-design` | Distinctive, production-grade UI when visuals matter. |
| `nextjs-turbopack` | Next.js 16+ and Turbopack vs webpack. |
| `bun-runtime` | Bun vs Node, tooling, deployment notes. |
| `documentation-lookup` | Prefer Context7 / current docs over stale training data. |
| `mcp-server-patterns` | Build MCP servers (Node/TS, tools, Zod, transports). |
| `e2e-testing` | Playwright, POM, CI, flaky tests. |
| `test-driven-development` | Classic TDD loop before implementation. |
| `tdd` | Test behavior via public interfaces (see `SKILL.md`). |
| `tdd-workflow` | Strong TDD + coverage expectations for features and refactors. |
| `systematic-debugging` | Debug methodology before proposing fixes. |
| `triage-issue` | Root-cause exploration → GitHub issue with TDD-oriented fix plan. |
| `security-review` | Auth, secrets, endpoints, payments — checklist. |
| `git-guardrails-claude-code` | Hooks to block destructive git commands in Claude Code. |
| `setup-pre-commit` | Husky, lint-staged, Prettier, typecheck (see `SKILL.md`). |
| `using-git-worktrees` | Isolated worktrees for features or plan execution. |
| `migrate-to-shoehorn` | Replace `as` in tests with `@total-typescript/shoehorn`. |

### Review and collaboration

| Skill folder | What it’s for |
|--------------|----------------|
| `requesting-code-review` | Before merge: ensure work meets intent. |
| `receiving-code-review` | Vet review comments before blindly applying. |
| `writing-skills` | Author, edit, or validate Agent Skills (`SKILL.md` format). |
| `write-a-skill` | Scaffold a new skill. |

### Research, writing, and content

| Skill folder | What it’s for |
|--------------|----------------|
| `deep-research` | Multi-source research with citations (firecrawl + exa MCPs). |
| `exa-search` | Neural search via Exa MCP. |
| `last30days` | Broad recent web + social coverage across many networks. |
| `market-research` | Market sizing, competitors, investor-style diligence. |
| `article-writing` | Long-form articles and guides in a defined voice. |
| `edit-article` | Structural and line edits on drafts. |
| `brand-voice` | Build a voice profile from real samples; reuse everywhere. |
| `content-engine` | Platform-native content systems and calendars. |
| `crosspost` | Adapt content per platform (X, LinkedIn, Threads, Bluesky). |
| `marketing-for-founders` | GTM, launch, first users, channels. |
| `video-editing` | Pipeline from footage through tools like FFmpeg, Remotion, Descript. |
| `frontend-slides` | HTML slides and PPT→web decks. |
| `fal-ai-media` | Image/video/audio via fal.ai MCP. |
| `x-api` | X/Twitter API usage patterns. |

### Fundraising and investors

| Skill folder | What it’s for |
|--------------|----------------|
| `investor-materials` | Decks, memos, models, consistent fundraising narrative. |
| `investor-outreach` | Cold/warm investor email and update drafts. |

### APIs, agents, and misc

| Skill folder | What it’s for |
|--------------|----------------|
| `claude-api` | Anthropic Messages API, streaming, tools, Agent SDK. |
| `obsidian-vault` | Search and manage Obsidian notes with wikilinks. |
| `agent-introspection-debugging` | Structured workflow when agent behavior fails. |
| `scaffold-exercises` | Course-style exercise folders with lint-clean stubs. |

---

## Suggested first session after `/onboard`

1. Skim **this file** end-to-end once.
2. Run **`/capabilities`** and ask questions about anything you will use weekly.
3. Open **`outputs/dashboards/cadence-hub.html`** in a browser for a static home screen (see `outputs/dashboards/README.md`).
4. Try **`/morning`** (or **`/context-prime`** then **`/research`** on a small topic) to exercise the stack.
5. Pick **one skill** that matches your job (e.g. `article-writing`, `api-design`) and open its `SKILL.md` so you know the depth available.

---

*Generated as part of Cadence. Update this file if you add commands, agents, or skills.*
