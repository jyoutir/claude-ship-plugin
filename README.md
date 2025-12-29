# Ship Workflow Plugin for Claude Code

A Claude Code plugin that helps you ship features with thorough PR reviews, commit messages, and Atlassian documentation.

## What it does

When you run `/ship`, Claude will:

1. **Thorough PR Review** - Analyzes your changes for code quality, bugs, security, and performance
2. **Commit Message** - Generates a concise commit message (you commit manually)
3. **Documentation** - Writes and pushes feature docs to Atlassian Confluence

## Installation

```bash
/plugin marketplace add jyoutir/claude-ship-plugin
/plugin install ship
```

## Usage

After completing a feature:

```
/ship
```

## Requirements

- Claude Code CLI
- Atlassian MCP configured (for documentation push)
