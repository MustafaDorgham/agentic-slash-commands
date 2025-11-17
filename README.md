# Agentic Slash Commands

A collection of intelligent slash commands for AI coding assistants ([Claude Code](https://claude.ai/code), Codex, Gemini CLI) optimised for JavaScript/TypeScript development workflows. Each command uses smart detection to identify project configuration and automatically execute appropriate tools with your preferred package manager.

**Multi-Platform Support**: Write commands once, use them across Claude Code, Codex, and Gemini CLI with platform-specific installers.

## Features

- **Multi-Platform Support**: Compatible with Claude Code, Codex, and Gemini CLI
- **Smart Package Manager Detection**: Automatically detects and uses pnpm, bun, yarn, or npm based on lock files
- **Framework Aware**: Recognises and adapts to React, Vue, Next.js, Nuxt, and more
- **Zero Configuration**: Works out of the box with standard JavaScript/TypeScript projects
- **Universal Installation**: One command installs for all supported platforms
- **Consistent Conventions**: All documentation and code follows English (Singapore/UK) spelling

## Available Commands

### Core Development

- **`/build`** - Intelligent build detection and execution
  - Auto-detects build tools (Webpack, Vite, Rollup, Next.js, etc.)
  - Uses detected package manager automatically

- **`/test`** - Smart test runner
  - Supports Jest, Vitest, Mocha, Cypress, Playwright
  - Provides clear pass/fail results with highlighted failures

- **`/lint`** - JavaScript/TypeScript linting and formatting
  - Runs ESLint and Prettier
  - Offers auto-fix when available

- **`/setup`** - Automated dependency installation
  - Intelligent package manager detection
  - Installs both production and development dependencies

### Project Management

- **`/clean`** - Safe cleanup of build artefacts
  - Removes node_modules, dist/, build/, .pnpm-store
  - Clears cache files safely

- **`/commit`** - Smart git commit creation
  - Balanced approach to grouping related changes
  - Generates descriptive commit messages

- **`/create-branch`** - Create and checkout new git branches
  - Smart validation
  - GitHub issue integration

- **`/create-issue`** - GitHub issue creation
  - Template support
  - Pre-filled with project context

- **`/create-pull-request`** - Automated PR creation
  - Analyses commits for description generation
  - Follows repository conventions

- **`/update-docs`** - Documentation maintenance
  - Updates CLAUDE.md and README.md
  - Keeps documentation in sync

## Installation

### Universal Installation (All Platforms)

Install commands for Claude Code, Codex, and Gemini CLI in one step:

```bash
git clone https://github.com/ruchernchong/agentic-slash-commands.git $HOME/agentic-slash-commands
cd $HOME/agentic-slash-commands
chmod +x install.sh
./install.sh
```

The universal installer will:
- Install commands for **Claude Code** (`$HOME/.claude/commands/`)
- Install commands for **Codex** (`$HOME/.codex/commands/`)
- Install commands for **Gemini CLI** (requires conversion to .toml format)

Commands will be immediately available globally across all projects.

### Platform-Specific Installation

To install for a specific platform only:

```bash
cd $HOME/agentic-slash-commands

# Claude Code only
bash scripts/install-claude.sh

# Codex only
bash scripts/install-codex.sh

# Gemini CLI only
bash scripts/install-gemini.sh
```

### Updating Commands

To update to the latest version across all platforms:

```bash
cd $HOME/agentic-slash-commands
git pull
```

No need to reinstall - the symlinks will automatically reflect the updates!

## Usage

Simply type `/` followed by the command name in your AI coding assistant:

**Claude Code:**
```
/build
/test
/lint
/setup
```

**Codex:**
```
/build
/test
/lint
/setup
```

**Gemini CLI:**
Commands work the same way after conversion to .toml format.

## How It Works

### Package Manager Detection

Commands automatically detect your package manager in this priority order:

1. **pnpm** (pnpm-lock.yaml present)
2. **bun** (bun.lockb present)
3. **yarn** (yarn.lock present)
4. **npm** (package-lock.json present or fallback)

### Smart Execution

Each command:
1. Analyses your project configuration (package.json, config files)
2. Detects the appropriate tool or framework
3. Selects the best package manager
4. Executes with optimal settings
5. Provides actionable feedback

## Command Architecture

Commands are organised in a modular structure supporting multiple platforms:

```
.
├── commands/          # All slash command definitions
│   ├── build.md
│   ├── test.md
│   ├── lint.md
│   ├── setup.md
│   ├── clean.md
│   ├── commit.md
│   ├── create-branch.md
│   ├── create-issue.md
│   ├── create-pull-request.md
│   └── update-docs.md
├── scripts/           # Platform installers and helper scripts
│   ├── install-claude.sh    # Claude Code installer
│   ├── install-codex.sh     # Codex installer
│   ├── install-gemini.sh    # Gemini CLI installer
│   └── commit               # Git commit helper script
├── lib/               # Shared utilities
│   └── helpers.sh     # Common bash functions for installers
├── CLAUDE.md          # Project guidance for Claude Code
├── README.md          # This file
└── install.sh         # Universal installer for all platforms
```

Each command file uses this format:

```yaml
---
description: Command description shown in Claude Code
allowed-tools: List of tools the command can use
---

Command instructions and logic here...
```

## Configuration

### Project-Specific Behaviour

Commands automatically adapt to:
- `package.json` scripts and dependencies
- Lock file detection (pnpm-lock.yaml, bun.lockb, yarn.lock, package-lock.json)
- ESLint and Prettier configuration
- Testing framework configuration
- Git repository state and GitHub templates

### Local Settings

Permission management can be configured in `.claude/settings.local.json`.

## Language Conventions

This repository follows **English (Singapore/UK)** spelling conventions:
- "organise" not "organize"
- "optimise" not "optimize"
- "behaviour" not "behavior"
- "colour" not "color"

## Contributing

Contributions are welcome! Please ensure:
- New commands follow the existing architecture pattern
- Documentation uses English (SG/UK) spelling
- Commands include smart detection where applicable
- YAML frontmatter is properly formatted

## License

MIT

## Acknowledgements

Built for [Claude Code](https://claude.ai/code) by Anthropic.
