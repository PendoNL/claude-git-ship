---
allowed-tools: Bash(git:*)
argument-hint: <branch>
description: Stage all changes, generate a commit message from the diff, and push to a branch
---

# Git Ship

Ship all changes to the specified branch with an AI-generated commit message.

## Instructions

1. First, check if there are any changes to commit:

Run `git status --short` to see the current state.

If the output is empty, inform the user: "No changes to ship. Working tree is clean." and stop here.

2. Stage all changes:

Run `git add -A` to stage everything.

3. Get the diff information:

Run `git diff --cached --stat` to get a summary of changes.

Then run `git diff --cached` to get the full diff content.

4. Analyze the diff and generate a commit message:

Based on the diff, create a commit message following these rules:
- Use conventional commit format with one of these prefixes:
  - `feat:` for new features
  - `fix:` for bug fixes
  - `docs:` for documentation changes
  - `style:` for formatting, whitespace, etc.
  - `refactor:` for code restructuring without behavior change
  - `test:` for adding or updating tests
  - `chore:` for maintenance tasks, dependencies, configs
  - `perf:` for performance improvements
  - `ci:` for CI/CD changes
  - `build:` for build system changes
- Subject line must be max 50 characters, imperative mood ("add" not "added")
- For complex changes, add a body separated by a blank line, wrapped at 72 chars
- Focus on "what" and "why", not "how"
- Be specific but concise

5. Create the commit:

Run `git commit -m "<your generated message>"` with the message you created.

If the message has a body, use:
```
git commit -m "<subject>" -m "<body>"
```

6. Push to the specified branch:

The target branch is: $ARGUMENTS

If no branch was specified, inform the user they need to provide a branch name (e.g., `/ship main`).

Run `git push origin $ARGUMENTS` to push the changes.

7. Confirm success:

Provide a brief summary:
- What was committed (the commit message)
- Which branch it was pushed to
- Number of files changed
