---
name: add-claim
description: Add an atomic insight to your knowledge graph. Claims are titled as declarative statements, not categories. Run as /add-claim [your insight].
---

Add this to my knowledge graph: $ARGUMENTS

## How to run this

1. Read `knowledge/03_projects/core-claims.md` to check for existing claims.

2. Process the claim:
   - **Format check**: Is it a specific, arguable, declarative statement? 
     - Good: "Shipped features are not delivered value."
     - Bad: "Product management insights."
   - **Duplicate check**: Does a similar claim already exist? If yes, ask: "This is similar to '[existing claim].' Is this a refinement, or a distinct new claim?"
   - **Contradiction check**: Does this contradict an existing claim? If yes, flag it: "This seems to conflict with '[existing claim].' Do you want to replace it, or do both stand?"

3. If the claim needs sharpening (vague, category-style): suggest a better title.
   Ask: "How about phrasing it as: '[sharpened version]'? Or stick with your original?"

4. **Append** the approved claim to `knowledge/03_projects/core-claims.md`.

5. Ask: "Any supporting evidence or context to add under this claim?"
   If yes, add it as a sub-note under the claim.

6. Confirm: "Added: '[claim]' to your knowledge graph."

## Claim title conventions

- Write as a complete sentence ending with a period
- Specific enough that it couldn't apply to every business
- Arguable — someone could reasonably disagree
- Yours — reflects your actual position, not received wisdom

Bad: "Customer focus matters."
Good: "Most SaaS companies confuse feature requests with customer focus."
