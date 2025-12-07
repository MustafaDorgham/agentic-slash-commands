# Contributing to Agentic Slash Commands

Thank you for considering contributing to this project! This repository provides intelligent agentic slash commands for multiple AI coding platforms (Claude Code, Codex, and Gemini CLI), designed to streamline JavaScript/TypeScript development workflows.

We welcome contributions of all kinds and appreciate your help in making these tools better for everyone.

## Code of Conduct

This project adheres to the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behaviour to the project maintainers.

## How to Contribute

We welcome several types of contributions:

- **New slash commands** - Add new workflow automation commands
- **New skills** - Create reusable capabilities that commands can leverage
- **Bug fixes** - Fix issues in existing commands, skills, or installation scripts
- **Documentation improvements** - Enhance README, CLAUDE.md, or command documentation
- **Test coverage expansion** - Add new test cases or improve existing tests
- **Installation script improvements** - Enhance the multi-platform installation system

## Getting Started

### Prerequisites

Before contributing, ensure you have:

- **Git** - For version control
- **Package manager** - npm, pnpm, bun, or yarn (pnpm preferred)
- **Docker** - Required for running the test suite
- **Bash/Zsh** - For running installation scripts

### Development Setup

1. **Fork the repository** on GitHub

2. **Clone your fork** locally:
   ```zsh
   git clone https://github.com/YOUR_USERNAME/agentic-slash-commands.git
   cd agentic-slash-commands
   ```

3. **Install for development**:
   ```zsh
   chmod +x install.sh
   ./install.sh
   ```
   This creates symlinks to `~/.claude/commands/`, `~/.codex/prompts/`, etc.

4. **Create a branch** for your changes:
   ```zsh
   git checkout -b feature/your-feature-name
   ```

## Development Workflow

### Repository Structure

```
.
├── commands/          # Slash command definitions (*.md with YAML frontmatter)
├── skills/            # Reusable skill definitions (*.md with YAML frontmatter)
├── scripts/           # Platform-specific installers and helpers
│   ├── install-claude.sh
│   ├── install-codex.sh
│   ├── install-gemini.sh
│   └── commit
├── tests/             # Docker-based testing infrastructure
│   ├── run-tests.sh
│   └── docker-compose.yml
├── .github/           # GitHub workflows and templates
│   ├── workflows/
│   └── ISSUE_TEMPLATE/
└── lib/               # Shared utilities
```

### Adding New Commands

Commands are markdown files with YAML frontmatter located in the `commands/` directory.

**Structure**:
```markdown
---
description: Brief description of what the command does
allowed-tools: Bash(git status), Bash(npm test), Read(*.json)
---

Command instructions here...
```

**Key principles**:

1. **YAML Frontmatter**:
   - `description`: Clear, concise explanation (shows in command list)
   - `allowed-tools`: Specific tools the command can use (e.g., `Bash(git add)`, `Read(*.ts)`)

2. **Smart Detection**:
   - Detect package manager from lock files (priority: pnpm-lock.yaml → bun.lockb → yarn.lock → package-lock.json)
   - Detect build tools, test frameworks, and project configuration
   - Avoid hardcoding specific tools (use detection logic)

3. **Package Manager Priority**:
   ```
   pnpm > bun > yarn > npm
   ```
   Always check for lock files and use the appropriate package manager.

**Example**: See `commands/build.md` or `commands/test.md` for reference implementations.

### Adding New Skills

Skills are reusable capabilities that commands can invoke programmatically. They differ from commands in that they're not directly user-facing.

**Structure**: Same as commands (YAML frontmatter + markdown)

**Difference from Commands**:
- **Commands**: User-facing slash commands (e.g., `/commit`, `/test`)
- **Skills**: Reusable logic invoked by commands (e.g., `commit-message-generator`, `project-structure-analyzer`)

**Integration Pattern**:
- Commands can reference and reuse skills
- Skills should be focused and single-purpose
- Skills enable DRY (Don't Repeat Yourself) across commands

**Example**: See `skills/commit-message-generator.md` or `skills/branch-name-validator.md`.

## Testing Requirements

**CRITICAL**: All contributions must pass the test suite before submission.

### Running Tests Locally

```zsh
cd tests
./run-tests.sh
```

This runs all tests in a Docker container (Alpine Linux environment).

### Test Types

- **Installation tests** - Validates symlink creation and correctness
- **Command validation** - Checks YAML frontmatter formatting
- **Idempotence tests** - Ensures repeated installations don't break setup
- **Platform tests** - Validates Claude Code, Codex, and Gemini CLI integration
- **Backup tests** - Verifies backup functionality works correctly

### Specific Test Runs

```zsh
# Run specific test suite
./run-tests.sh docker    # Docker-based tests only
./run-tests.sh macos     # macOS tests only

# Rebuild Docker image before testing
./run-tests.sh --build
```

### CI/CD Requirements

GitHub Actions will automatically run tests on your PR. The following must pass:

- **docker-tests** - Alpine Linux container tests
- **macos-tests** - macOS environment tests
- **validate-commands** - YAML frontmatter validation

See `.github/workflows/tests.yml` for the complete CI/CD pipeline.

## Code Style Guidelines

### Commit Message Format

Use **short, descriptive commit messages** (max 50 characters) that focus on **what** changed:

**Good examples** (from recent commits):
- `Add Contributor Covenant Code of Conduct`
- `Add natural language title guidelines to PR command`
- `Update docs to use zsh instead of bash`
- `Fix installation error on macOS`

**Format**:
- Start with a verb (Add, Update, Fix, Remove, Refactor)
- Be specific about what changed
- Keep it concise (≤50 characters)

### Markdown Formatting

- Use proper heading hierarchy (`#`, `##`, `###`)
- Include code blocks with language hints (```zsh, ```markdown)
- Use **bold** for emphasis, `code` for commands/paths
- Add blank lines between sections for readability

### Bash Scripting Conventions

- Use `#!/usr/bin/env bash` or `#!/usr/bin/env zsh` shebang
- Include error handling (`set -e`)
- Add comments for complex logic
- Use descriptive variable names
- Quote variables to prevent word splitting

## Pull Request Process

1. **Create a feature branch**:
   ```zsh
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes** following the guidelines above

3. **Run tests locally**:
   ```zsh
   cd tests && ./run-tests.sh
   ```

4. **Commit your changes**:
   ```zsh
   git add .
   git commit -m "Add your short message here"
   ```

5. **Push to your fork**:
   ```zsh
   git push origin feature/your-feature-name
   ```

6. **Create a Pull Request** on GitHub:
   - Fill out the PR template (auto-populated)
   - Link any related issues (e.g., "Closes #123")
   - Provide clear description of changes
   - Ensure all CI/CD checks pass

7. **Respond to review feedback**:
   - Address reviewer comments
   - Push additional commits to your branch
   - Request re-review when ready

## Documentation Requirements

When contributing, update relevant documentation:

- **README.md** - Add new commands/skills to the command list
- **CLAUDE.md** - Update if changing architecture or adding new patterns
- **Inline comments** - Add comments for complex logic or non-obvious behaviour
- **CONTRIBUTING.md** (this file) - Update if changing the contribution process

## Questions & Help

- **General questions** - Use [GitHub Discussions](../../discussions) for community Q&A
- **Bug reports** - Create a [GitHub Issue](../../issues/new/choose) with the bug report template
- **Feature requests** - Create a [GitHub Issue](../../issues/new/choose) with the feature request template

---

Thank you for contributing! Your efforts help improve the development experience for developers using AI coding assistants across multiple platforms.
