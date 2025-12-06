---
description: Update a GitHub issue with new title, body, labels, or assignees
allowed-tools: Bash(gh issue view), Bash(gh issue edit), Bash(gh repo view)
---

## Language Conventions

**Infer language style from the project:**
- Analyze existing issues, documentation, and commit messages to detect the project's language variant (US English, UK English, etc.)
- Match the spelling conventions found in the project (e.g., "initialize" vs "initialise", "behavior" vs "behaviour")
- Maintain consistency with the project's established language style throughout issue updates

---

Update a GitHub issue with the following workflow:

1. Check if we're in a GitHub repository
2. **Identify the issue to update:**
   - If an issue number is provided (e.g., "issue 123", "#456", or "789"), use that issue
   - Otherwise, ask the user for the issue number
3. **View current issue details:**
   - Display the issue title, body, labels, assignees, and state
   - Check for ISSUE_TEMPLATE format in the repository to understand the issue structure
4. **Determine what to update:**
   - Ask what fields the user wants to update (title, body, labels, assignees, state)
   - Accept input for new values
5. **Update the issue:**
   - For body updates, respect ISSUE_TEMPLATE format if the original issue follows it
   - Only use labels that already exist in the repository
   - Only assign users who are valid repository collaborators
   - Use `gh issue edit` to apply changes
6. **Confirm changes:**
   - Show a summary of all updates before applying
   - Display success message with link to updated issue

For the issue title:
- Use natural, descriptive language
- Keep it concise but informative
- Match the style of existing issue titles in the repository

For the issue body (when using ISSUE_TEMPLATE format):
- Follow the exact template structure
- Preserve required sections and formatting
- Update only the sections being changed
- Maintain template sections

For labels and assignees:
- Only add labels that already exist in the repository
- Validate assignees are valid repository collaborators
- Show current labels and assignees before making changes
