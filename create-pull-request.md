---
description: Push branch and create GitHub pull request
allowed-tools: Bash(git status), Bash(git push), Bash(git log), Bash(git diff), Bash(gh pr create), Bash(gh pr list), Bash(git branch)
---

## Language Conventions

All PR titles and descriptions should use **English (Singapore)** or **English (UK)** spelling:
- Use "s" instead of "z" (organise, optimise, analyse)
- Use "our" endings (colour, behaviour, favour)
- Use "re" endings (centre, metre)

---

Create a pull request with the following workflow:

1. Check current git status and branch
2. Push the current branch to remote (with -u flag if needed)
3. Analyse recent commits to generate PR title and description
4. Create GitHub PR using `gh pr create`

**CONCISE PR RULE: Keep everything brief and focused**

Generate a short, clear title based on the commit history and user's request context.

For the PR description:
- **Maximum 1-2 bullet points** summarizing the key changes
- **No verbose explanations** - be direct and specific
- **No test plan, acceptance criteria, or additional sections**
- Focus only on what changed and why

