# Signal Tracker

Live intelligence on prospects, contacts, and opportunities. Scored and decayed weekly.

Updated by `/weekly` (decay check) and manually when new signals are observed.
Score any entry with `/score [name]` or by invoking the `signal-scoring` skill.

---

<!-- SIGNAL FORMAT — one entry per prospect:

## [Name] — [Company] — [Role]

**ICP fit:** strong / partial / unclear
**Last scored:** YYYY-MM-DD | **Score:** [X] | **Tier:** HOT / WARM / NURTURE / COLD

### Active Signals

| Signal | Date observed | Base | Decay | Effective |
|--------|--------------|------|-------|-----------|
| [type] | YYYY-MM-DD | [pts] | [multiplier] | [score] |

**Combination bonus:** yes / no

### Notes
[Context, conversation history, next step]

### History
- YYYY-MM-DD: [what happened]

---

DECAY REMINDER:
- 0–14 days: 1.0x (fresh)
- 15–45 days: 0.65x (aging)
- 46–90 days: 0.35x (stale)
- 91–180 days: 0.15x (cold)
- 180+ days: 0x — remove from active tracking

TIERS:
- 65+: HOT — reach out this week
- 35–64: WARM — reach out this month
- 15–34: NURTURE — monitor, check back in 30 days
- <15: COLD — deprioritize
-->

## [Prospect Name] — [Company] — [Title]

**ICP fit:** [strong / partial / unclear]
**Last scored:** YYYY-MM-DD | **Score:** — | **Tier:** —

### Active Signals

| Signal | Date observed | Base | Decay | Effective |
|--------|--------------|------|-------|-----------|
| [Add first signal] | YYYY-MM-DD | — | — | — |

### Notes
[What you know about this person and what they need]

---
