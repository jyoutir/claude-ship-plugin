---
allowed-tools: Bash(git:*), Read, Grep, mcp__atlassian__*
description: Thorough PR review, commit message, and push docs to Atlassian
---

# Ship Workflow

You are helping the user ship a completed feature. Follow these steps carefully.

## Step 1: Thorough PR Review

1. Run `git diff` to see all changes (or `git diff --staged` if staged)
2. Read the changed files fully to understand the context
3. Perform a **thorough code review** checking:
   - **Code quality**: Readability, naming, structure
   - **Bugs**: Edge cases, null checks, error handling
   - **Security**: Input validation, injection risks, auth issues
   - **Performance**: Unnecessary loops, memory leaks, N+1 queries
   - **Best practices**: DRY, SOLID, Flutter/Dart conventions

4. Present your review with:
   - Summary of what changed
   - Specific improvement suggestions with line references
   - Questions about unclear logic

5. Discuss with the user and iterate until they're satisfied.

## Step 2: Commit Message

1. Generate a **concise 1-2 line commit message**:
   - Imperative mood: "Add", "Fix", "Update"
   - Max 50 chars first line
   - Be specific but concise

2. Present the message. User will commit manually.

## Step 3: Documentation

1. Ask: "Where should I push the docs?" (Confluence space/page)
2. Ask: "What problem does this feature solve?"

3. Write documentation following this format:

**Problem:** [1-2 sentences - what user pain does this address?]

**Solution:** [1-2 sentences - what was built?]

---

## Overview
[Brief description]

## How It Works
[Key functionality + code paths]

## Usage
[Example code or steps]

## Notes
[Edge cases, limitations, related features]

4. Show the draft to user for approval.
5. Push to Atlassian after confirmation.
