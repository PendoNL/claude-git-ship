# git-ship

A Claude Code plugin that streamlines your git workflow by staging all changes, generating an AI-powered commit message based on the actual diff, and pushing to a branch — all in one command.

## Installation

```
/plugin install github:PendoNL/claude-git-ship
```

## Usage

```
/ship <branch>
```

### Examples

```
/ship main
/ship develop
/ship feature/new-login
```

## What It Does

When you run `/ship <branch>`, the plugin:

1. **Checks for changes** — Runs `git status` to see if there's anything to commit
2. **Stages everything** — Runs `git add -A` to stage all changes
3. **Analyzes the diff** — Gets both the summary and full diff of staged changes
4. **Generates a commit message** — Creates a professional commit message based on the actual changes
5. **Commits** — Creates the commit with the generated message
6. **Pushes** — Pushes to your specified branch

## Commit Message Format

The plugin generates commit messages using the [Conventional Commits](https://www.conventionalcommits.org/) specification:

| Prefix | Use Case |
|--------|----------|
| `feat:` | New features |
| `fix:` | Bug fixes |
| `docs:` | Documentation changes |
| `style:` | Formatting, whitespace |
| `refactor:` | Code restructuring |
| `test:` | Adding or updating tests |
| `chore:` | Maintenance, dependencies |
| `perf:` | Performance improvements |
| `ci:` | CI/CD changes |
| `build:` | Build system changes |

Commit messages follow best practices:
- Subject line max 50 characters
- Imperative mood ("add feature" not "added feature")
- Body wrapped at 72 characters for complex changes
- Focuses on "what" and "why", not "how"

## Requirements

- Git must be installed and available in your PATH
- You must be in a git repository
- You must have push access to the remote

## License

MIT License - see [LICENSE](LICENSE) for details.
