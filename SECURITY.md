# Security Policy

## Our Commitment

We take the security of this project seriously. As an installer tool that creates symlinks and runs on user systems, we're committed to ensuring the safety and integrity of all installation scripts, commands, and skills.

## Supported Versions

This project follows a **rolling release model**. The `main` branch is the only supported version.

| Version | Supported          |
| ------- | ------------------ |
| main    | :white_check_mark: |

To ensure you have the latest security fixes and updates:

```zsh
cd ~/agentic-slash-commands
git pull
```

The symlink-based installation means updates are immediately available across all platforms without reinstallation.

## Reporting a Vulnerability

We use GitHub's Security Advisory feature for private vulnerability reporting.

### How to Report

1. Navigate to the [Security Advisories page](../../security/advisories)
2. Click "Report a vulnerability"
3. Fill out the advisory form with detailed information

### What to Include

Please include as much information as possible:

- **Description** - Clear explanation of the vulnerability
- **Steps to reproduce** - Detailed steps to trigger the issue
- **Potential impact** - What could an attacker achieve?
- **Affected platforms** - Claude Code, Codex, Gemini CLI, or all?
- **Suggested fix** - If you have ideas for remediation

### Response Timeline

- **Initial response**: Within 48-72 hours
- **Status update**: Within 7 days
- **Fix timeline**: Depends on severity and complexity

We'll keep you informed throughout the process and credit you in the security advisory (unless you prefer to remain anonymous).

## Security Considerations

### Symlink Safety

Our installation scripts include several safety measures:

- **Validation checks** - Scripts verify symlink targets exist before creation
- **Broken link detection** - Tests identify and report broken symlinks
- **Backup functionality** - Auto-backup before overwriting existing files
- **Idempotence testing** - Multiple installations don't break existing setup

### Installation Verification

The test suite (`tests/run-tests.sh`) validates:

- Symlinks point to valid files in the repository
- No broken or dangling symlinks after installation
- Repeated installations produce consistent results
- Backup files are created correctly

### Multi-Platform Safety

Each platform has dedicated installation scripts:

- `scripts/install-claude.sh` - Claude Code only
- `scripts/install-codex.sh` - Codex only
- `scripts/install-gemini.sh` - Gemini CLI only

This separation prevents cross-platform contamination and ensures platform-specific behaviour is isolated.

### CI/CD Security

Our GitHub Actions workflows follow security best practices:

- **Pinned Actions** - All actions pinned to commit hashes (not floating tags)
- **No floating versions** - Prevents supply chain attacks via action updates
- **Minimal permissions** - Workflows use least-privilege access
- **Automated testing** - All changes validated before merge

See `.github/workflows/tests.yml` for our CI/CD security configuration.

### Dependency Management

This project minimises external dependencies:

- **Core tools only** - Relies on git, bash/zsh, and Docker for testing
- **No npm dependencies** - Pure bash/markdown implementation
- **Regular audits** - Periodic review of all scripts and dependencies

## Best Practices for Users

To use this project securely:

1. **Clone from official repository**:
   ```zsh
   git clone https://github.com/ruchernchong/agentic-slash-commands.git
   ```

2. **Review installer scripts** before running:
   ```zsh
   cat install.sh
   cat scripts/install-claude.sh
   ```

3. **Verify symlinks** after installation:
   ```zsh
   ls -la ~/.claude/commands/
   ls -la ~/.codex/prompts/
   ```

4. **Keep repository updated**:
   ```zsh
   cd ~/agentic-slash-commands
   git pull
   ```

5. **Run tests** to verify integrity:
   ```zsh
   cd tests && ./run-tests.sh
   ```

## Disclosure Policy

We follow **coordinated disclosure**:

1. **Report received** - Acknowledge within 48-72 hours
2. **Investigation** - Assess severity and impact
3. **Fix developed** - Create and test patch
4. **Coordinated release** - Agree on public disclosure timeline with reporter
5. **Public advisory** - Publish security advisory with credit to reporter
6. **CVE assignment** - Request CVE if applicable

### Credit

We believe in recognising security researchers. If you report a vulnerability, we'll:

- Credit you in the security advisory (unless you prefer anonymity)
- Thank you in the commit message fixing the issue
- Add you to our security acknowledgements (if you'd like)

---

Thank you for helping keep this project secure!
