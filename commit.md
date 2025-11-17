---
description: Smart git commit with short, concise messages
allowed-tools: Bash(git status), Bash(git add), Bash(git diff), Bash(git commit), Bash(git log)
---

## Language Conventions

All commit messages, code comments, and documentation should use **English (Singapore)** or **English (UK)** spelling:
- Use "s" instead of "z" (organise, optimise, analyse)
- Use "our" endings (colour, behaviour, favour)
- Use "re" endings (centre, metre)

---

Create git commits with a balanced approach - keep related changes together, split only when potentially huge:

**COMMIT MESSAGE RULE: ALWAYS use short messages (max 50 characters)**

1. Pull latest changes from remote to ensure branch is up to date (git pull)
2. Show current git status and analyse all changes
3. Assess the scope of changes:
   - **Small to medium changes**: Keep related changes in a single commit
   - **Large changes**: Only split when the changeset is potentially huge and mixing unrelated functionality
4. For normal commits:
   - Stage all related changes together
   - Create ONE short, descriptive commit message (max 50 characters)
   - Focus on the main purpose of the change
5. For huge changesets only:
   - Group by major functional areas
   - Stage files by logical groups
   - Create separate commits for distinct features/fixes

**Commit Message Requirements (ALWAYS ENFORCE):**
- **Maximum 50 characters** - no exceptions
- Use present tense verbs (add, fix, update, remove, refactor)
- Be specific but concise (e.g., "fix auth redirect bug", "add user search")
- Prefer cohesive commits over artificially split ones

This approach maintains clean git history with consistently short, readable commit messages.

