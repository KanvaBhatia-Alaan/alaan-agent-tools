# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Claude Code plugin named **alaan-agent-tools** that extends Claude Code with development workflow automation commands, coding guidelines.

## Repository Structure

```
.claude/
├── commands/          # Custom commands for Claude Code
│   ├── review-changes.md
│   ├── create-pr.md
│   └── create-intermediate-pr.md
├── skills/           # Reusable skills
│   └── karpathy-guidelines/

.claude-plugin/
├── plugin.json       # Plugin configuration
└── marketplace.json  # Marketplace metadata
```

## Custom Commands

### review-changes
Reviews current branch changes against a target branch (default: `origin/master`). Performs code review focused on:
- Logic and correctness
- Readability and maintainability
- Performance concerns
- Test coverage
- Provides structured feedback in table format

### create-pr
Commits changes and creates a PR:
1. Reviews uncommitted changes via `git diff`
2. Commits changes
3. Pushes to origin
4. Creates PR using `gh pr create --base master`
- Title kept under 80 characters
- Description under five sentences

### create-intermediate-pr
Creates PRs against `uat` or `staging` branches with merge conflict resolution:
1. Validates current branch is `feature/*` or `hotfix/*`
2. Ensures branch is not behind master (reverse merges if needed)
3. Creates intermediate branch: `intermediate/[current-branch]_[target]`
4. Reverse merges target branch and resolves conflicts
5. Pushes and creates PR

**Branch naming convention**:
- Features: `feature/aim-123-description`
- Hotfixes: `hotfix/aim-123-description`
- Intermediates: `intermediate/feature/aim-123-description_uat`

## Skills

### karpathy-guidelines
Behavioral guidelines for better code quality:
1. **Think Before Coding**: Surface assumptions and tradeoffs explicitly
2. **Simplicity First**: Minimum code, no speculative features
3. **Surgical Changes**: Only modify what's necessary
4. **Goal-Driven Execution**: Define verifiable success criteria

Use this skill when writing, reviewing, or refactoring code.

## Development Notes

- Target branch is typically `origin/master` unless otherwise specified
- Always use GitHub CLI (`gh`) for PR operations
- Follow existing commit message patterns in the repository
- When resolving merge conflicts in intermediate branches, ensure all conflicts are properly resolved before pushing
