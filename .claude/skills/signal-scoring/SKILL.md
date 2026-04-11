---
name: signal-scoring
description: Use when evaluating a prospect, contact, or opportunity — scores their readiness based on observed signals, applies decay based on signal age, and returns a prioritized action recommendation. Also use during /weekly to audit the signal tracker for stale entries.
---

# Signal Scoring

Score prospects based on what you've actually observed — not gut feel. Signals decay. A funding announcement from last week is worth 3x the same announcement from three months ago.

## How to Use

1. Read `knowledge/00_user-brain/signal-tracker.md` for existing signals on this prospect
2. Read `knowledge/00_user-brain/living-brain.md` for current ICP definition and goals
3. Score the prospect using the framework below
4. Return a score, tier, and recommended action
5. Offer to update `signal-tracker.md` with any new signals identified

---

## Signal Types and Base Scores

| Signal | Base Score | What it means |
|--------|-----------|---------------|
| Direct engagement (replied, clicked, attended) | 40 | They took an action — highest intent |
| Referral (warm intro from trusted contact) | 40 | Trust transfer — changes the conversation |
| Intent signal (pricing page, trial, content download) | 35 | Active evaluation underway |
| Leadership change (new decision-maker, role created) | 25 | New buyer, window of influence open |
| Funding event (raise, Series A/B/C, grant) | 25 | Budget available, growth mode |
| Trigger event (restructure, M&A, IPO, pivot) | 25 | Change creates urgency |
| Tool stack change (adopted adjacent tool, left competitor) | 20 | Movement in your problem space |
| Hiring signal (role posted that indicates pain or priority) | 20 | Pain made visible |
| Content engagement (liked, shared, commented on your content) | 15 | Passive awareness |

---

## Decay Function

Signal age degrades value. Apply these multipliers:

| Age | Multiplier | Label |
|-----|-----------|-------|
| 0–14 days | 1.0x | Fresh |
| 15–45 days | 0.65x | Aging |
| 46–90 days | 0.35x | Stale |
| 91–180 days | 0.15x | Cold |
| 180+ days | 0x | Expired — remove from active scoring |

**Combination bonus:** If a prospect has 2+ independent signals (different types), add 15% to total score. Three or more signals: add 25%.

---

## Scoring Formula

```
Signal Score = Σ(Base Score × Decay Multiplier) × Combination Bonus
```

---

## Tiers and Actions

| Score | Tier | Recommended Action |
|-------|------|--------------------|
| 65+ | 🔴 HOT | Reach out this week. Personalize to the signal. Don't wait. |
| 35–64 | 🟡 WARM | Reach out this month. Add value before asking. |
| 15–34 | 🔵 NURTURE | Stay visible. Monitor for new signals. Check back in 30 days. |
| <15 | ⚪ COLD | Deprioritize. Only re-engage if a fresh signal appears. |

---

## Output Format

Return:

```
## Signal Score: [Name]

**Total Score:** [X] → [TIER]

**Signals:**
| Signal | Age | Base | Decay | Effective |
|--------|-----|------|-------|-----------|
| [type] | [N days] | [base] | [multiplier] | [score] |

**Combination bonus:** [yes/no — X%]

**Recommended action:** [specific next step based on tier and signals]

**Suggested outreach angle:** [what to reference, what to lead with]
```

---

## During Weekly Review

When called from `/weekly`, scan `signal-tracker.md` for:
- Any signals now 180+ days old → mark expired, propose removal
- Any prospects whose total score dropped below 15 since last week → flag for deprioritization
- Any prospects with 2+ fresh signals → surface as new HOT tier
- Overall pipeline health: how many HOT / WARM / NURTURE / COLD

Return a brief pipeline health summary as part of the weekly output.
