---
allowed-tools: Bash(gh issue view:*), Bash(gh search:*), Bash(gh issue list:*), Bash(gh pr comment:*), Bash(gh pr diff:*), Bash(gh pr view:*), Bash(gh pr list:*)
description: Code review a pull request
---

Provide a code review for the given pull request.

Follow these steps:

1. Use a Haiku agent to check if the pull request (a) is closed, (b) is a draft, (c) does not need review (automated PR, trivially simple), or (d) already has a review from you. If so, stop.
2. Use a Haiku agent to get a summary of the change.
3. Launch 3 parallel Sonnet agents to independently review:
   - Agent 1: CLAUDE.md compliance
   - Agent 2: Bug detection (logic errors, null handling, security)
   - Agent 3: Code quality (duplication, error handling, test coverage)
4. Filter to issues with confidence ≥ 80. If none, do not proceed.
5. Comment on the PR with findings.

Output format:

---
### Code review

Found N issues:

1. <description> — <file:line>
2. <description> — <file:line>

🤖 Generated with [Claude Code](https://claude.ai/code)

---

If no issues: "No issues found. Checked for bugs and CLAUDE.md compliance."
