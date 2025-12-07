<!--
PR Title Guidelines:
- Use natural language that clearly describes the change
- Good: "Add dark mode support to build command"
- Good: "Fix installation error on macOS"
- Avoid: "Update files" or "Bug fix"
-->

## Description

<!-- Provide a clear description of your changes -->

Closes #<!-- issue number, if applicable -->

## Type of Change

<!-- Check all that apply -->

- [ ] New command
- [ ] New skill
- [ ] Bug fix
- [ ] Documentation update
- [ ] Installation script improvement
- [ ] Test coverage expansion
- [ ] Other (please describe):

## Affected Components

<!-- Check all that apply -->

- [ ] Commands (slash commands)
- [ ] Skills (reusable capabilities)
- [ ] Installation scripts
- [ ] Testing infrastructure
- [ ] CI/CD workflows
- [ ] Documentation

## Testing Checklist

<!-- Ensure all applicable items are checked -->

- [ ] Tests pass locally (`cd tests && ./run-tests.sh`)
- [ ] New tests added (if applicable)
- [ ] Tested on target platforms:
  - [ ] Claude Code
  - [ ] Codex
  - [ ] Gemini CLI (if applicable)
- [ ] YAML frontmatter validated (for command/skill changes)

## Documentation Checklist

<!-- Update relevant documentation -->

- [ ] README.md updated (if adding new command/skill)
- [ ] CLAUDE.md updated (if changing architecture)
- [ ] Inline comments added for complex logic
- [ ] CONTRIBUTING.md updated (if changing contribution process)

## Code Quality Checklist

<!-- Ensure code follows project standards -->

- [ ] Follows existing code style
- [ ] Smart detection implemented (where applicable)
- [ ] No hardcoded package managers (uses detection logic)
- [ ] Commit messages follow project conventions (≤50 characters)

## Additional Notes

<!-- Optional: Add any additional context -->

### Breaking Changes
<!-- Describe any breaking changes -->

### Migration Notes
<!-- Describe how users should migrate (if applicable) -->

### Related PRs
<!-- Link to related pull requests -->

### Screenshots
<!-- Add screenshots for documentation changes -->
