# Ship Plugin for Claude Code

A workflow plugin for shipping features with thorough PR review, commit messages, and Atlassian documentation.

## What it does

`/ship` runs a 3-step workflow:

1. **Thorough PR Review** - Code quality, bugs, security, performance checks
2. **Commit Message** - Generates concise commit message (you commit manually)
3. **Documentation** - Writes & pushes docs to Confluence/Atlassian

## Installation

```
/plugin install your-username/claude-ship-plugin
```

## Requirements

- Atlassian MCP plugin enabled (for pushing docs)
- Run `npx -y mcp-remote https://mcp.atlassian.com/v1/sse` to authenticate

## Usage

After finishing a feature:

```
/ship
```

## Files

- `commands/ship.md` - Main /ship command
- `skills/ship/COMMIT_STANDARDS.md` - Commit message guidelines
- `skills/ship/DOC_TEMPLATE.md` - Documentation format template
