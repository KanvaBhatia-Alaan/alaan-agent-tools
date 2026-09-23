# Alaan Agent Tools

A Claude Code plugin that provides workflow automation commands, coding guidelines, for daily development tasks.

## Features

- **Code Review Automation**: Review changes against target branches with structured feedback
- **PR Creation**: Streamlined PR creation with automatic commit, push, and GitHub CLI integration
- **Intermediate Branch Management**: Handle complex merge scenarios for staging/UAT deployments
- **Coding Guidelines**: Karpathy guidelines skill for better code quality
- **Visual Explainers**: ELI5 skill that turns any topic into a picture-first HTML artifact

## Installation

### Plugin (Recommended)

```bash
# Add the marketplace
/plugin marketplace add KanvaBhatia-Alaan/alaan-agent-tools

# Install the plugin
/plugin menu
```

Select `alaan-agent-tools` from the menu. Restart Claude Code after installation.

### Manual (Advanced)

```bash
git clone https://github.com/KanvaBhatia-Alaan/alaan-agent-tools.git
cd alaan-agent-tools
cp -r .claude/* ~/.claude/
cp -r .claude-plugin/* ~/.claude-plugin/
```

Restart Claude Code after installation.

## Available Commands

### `/review-changes`
Review current changes against a target branch (default: `origin/master`).

**What it does:**
- Fetches diff using GitHub CLI
- Analyzes logic, correctness, and performance
- Checks for test coverage
- Provides structured feedback with line numbers and solutions

### `/create-pr`
Create a pull request from the current branch.

**What it does:**
1. Reviews uncommitted changes
2. Commits and pushes changes
3. Creates PR with concise title and description
4. Uses `gh pr create --base master` by default

### `/create-intermediate-pr`
Create an intermediate branch for PRs against `uat` or `staging`.

**What it does:**
1. Validates branch naming (`feature/*` or `hotfix/*`)
2. Ensures branch is up-to-date with master
3. Creates `intermediate/[branch-name]_[target]` branch
4. Handles reverse merge and conflict resolution
5. Creates PR to target branch

**Use case:** When merging to staging/UAT that has diverged from master.

## Available Skills

### `/karpathy-guidelines`
Apply Andrej Karpathy's behavioral guidelines for better code quality:
- Think before coding (surface assumptions)
- Simplicity first (no speculative features)
- Surgical changes (minimal modifications)
- Goal-driven execution (verifiable success criteria)

Use when writing, reviewing, or refactoring code.

### `/eli5`
Explain anything like you're 5 - as a picture book, not a wall of text.

**What it does:**
1. Researches the topic first (reads the real code/files, never guesses)
2. Compresses it into 5-7 beats on one everyday metaphor
3. Builds an HTML page of huge self-contained visuals (inline SVG, mermaid, emoji scenes)
4. Enforces a hard word budget - under 150 words of prose, jargon confined to a glossary strip
5. Publishes it as an artifact and hands back the link

**Use case:** Onboarding someone to a subsystem, or understanding an unfamiliar flow at a glance.

## Requirements

- Claude Code CLI
- GitHub CLI (`gh`) for PR operations
- Git configured with appropriate credentials

## Author

**Kanva Bhatia**
- GitHub: [@KanvaBhatia-Alaan](https://github.com/KanvaBhatia-Alaan)

## Support

For issues, feature requests, or contributions, please visit the [GitHub repository](https://github.com/KanvaBhatia-Alaan/alaan-agent-tools).
