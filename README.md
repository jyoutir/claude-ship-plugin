# Ship Workflow Plugin for Claude Code

Ship code while building deep understanding of your changes.

## What it does

1. **Code Review** - Bugs, security, performance issues with file:line references
2. **Structure Review** - Analyzes codebase patterns, suggests feature-first architecture improvements
3. **Commit Message** - Conventional commit format
4. **Understanding Quiz** - Research-backed questions (Bloom's Taxonomy) to build lasting mental models
5. **Confluence Docs** - Optional documentation push

## Installation

```bash
/plugin marketplace add jyoutir/claude-ship-plugin
/plugin install ship
```

## Usage

```
/ship
```

## Requirements

- Claude Code CLI
- Atlassian MCP configured (for documentation push)
