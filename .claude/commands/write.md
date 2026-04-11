---
name: write
description: Research → outline → draft → voice check pipeline. Produces content in your voice. Run as /write [type: post/memo/thread/email/brief] [topic].
---

Write: $ARGUMENTS

## How to run this

1. Parse the request: what type of content, what topic, what audience (if specified).

2. Read these files before writing anything:
   - `context/VOICE_CALIBRATION.md` — your voice, style, words to use/avoid
   - `knowledge/01_style-guides/voice.md` — writing patterns
   - `knowledge/01_style-guides/anti-patterns.md` — what to avoid
   - `knowledge/01_style-guides/kill-criteria.md` — what makes content not worth publishing
   - `knowledge/03_projects/core-claims.md` — what this content should ladder back to

3. **Research phase** (if topic needs research):
   Dispatch a **researcher** agent to gather relevant context and evidence. Return key facts and examples to inform the draft.

4. **Outline phase**:
   Draft a brief outline: opening hook, core argument, key points, closing. 
   Show it to the user: "Here's the structure I'm thinking. Good to proceed?"

5. **Draft phase** (after outline approval):
   Write the full draft. Apply:
   - Their voice from VOICE_CALIBRATION.md
   - Their argument structure
   - Their vocabulary (words to use, words to never use)
   - Their anti-patterns (what to avoid)

6. **Voice check** (before returning):
   Re-read the draft against VOICE_CALIBRATION.md. Check:
   - Does this sound like them?
   - Any banned words slipped in?
   - Does the structure match their argument style?
   - Does it ladder back to a core claim?
   
   If the voice check fails on any point, fix it before showing the draft.

7. Return the draft with a brief note: "Voice check passed. [Any specific notes on choices made]."

8. Save to `outputs/[type]_[topic-slug]_v1.md`

9. Ask: "Want to sharpen anything? I can run this in Sharpening mode."

## Content type conventions

- **post** — LinkedIn/social. 150-300 words. Hook → insight → implication.
- **thread** — Twitter/X thread. 5-8 tweets. Each tweet standalone but connected.
- **memo** — Internal strategy doc. Problem → analysis → recommendation → risks.
- **email** — Professional email. Context → point → ask. Short.
- **brief** — Executive summary. Bottom line first. Bullets for support.
- **article** — Long-form. 800-1500 words. Argument-led, not listicle.
