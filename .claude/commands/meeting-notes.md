---
name: meeting-notes
description: Convert a meeting transcript into structured notes. Paste the transcript after running this command, or provide a file path.
---

Process meeting notes from: $ARGUMENTS

If no arguments provided, ask: "Paste your transcript below, or provide a file path."

## How to run this

1. Read `meeting-notes/INDEX.md` and `meeting-notes/PEOPLE.md` for context on participants.
2. Read the transcript (pasted or from file).

3. Extract:
   - **Meeting metadata**: date, attendees, type (1:1, team review, external, etc.), duration estimate
   - **Summary**: 2-3 sentences — what was discussed and decided
   - **Key decisions**: explicit choices made
   - **Action items**: who owns what, by when (if stated)
   - **Knowledge candidates**: any insights, claims, or principles worth preserving

4. Format as:

---

## [Date] | [Meeting Title] | [Duration estimate]

**Attendees:** [Names]
**Type:** [1:1 / strategy / review / external / team standup / other]
**Tags:** #[topic] #[project]

### Summary
[2-3 sentences: what was discussed and decided]

### Key Decisions
- [Decision 1]
- [Decision 2]

### Action Items
- [ ] @[Person] — [Task] — due [date if mentioned]

### Notes
[Any additional context worth preserving]

---

5. **Append** this entry to `meeting-notes/YYYY-MM.md` (create the file if it doesn't exist for this month).

6. **Update** `meeting-notes/INDEX.md` with a one-line entry:
   `YYYY-MM-DD | [Title] | [Duration] | #tags`

7. **Update** `meeting-notes/PEOPLE.md` if any new people appeared or new context emerged about existing people.

8. If knowledge candidates were identified: ask "I noticed something worth capturing — [claim]. Should I add this to your knowledge graph?"

9. Confirm: "Notes saved to `meeting-notes/YYYY-MM.md`. Action items: [list]."
