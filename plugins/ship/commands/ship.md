---
allowed-tools: Bash(git:*), Read, Grep, AskUserQuestion, WebSearch, WebFetch, mcp__atlassian__*
description: Code review, quiz to deepen understanding, and push docs to Atlassian
---

# Ship Workflow

Help the user ship code while building **deep, lasting understanding** of their changes and codebase.

## Step 1: Analyze Changes

1. Run `git diff` (or `git diff --staged`) to see all changes
2. Read changed files AND surrounding context:
   - What files import/depend on these changes?
   - What's the data flow through these components?
   - What patterns/libraries are being used?
3. If new libraries/APIs, WebSearch for docs and best practices
4. Build a mental model: WHAT changed, WHY it matters, HOW it connects

## Step 2: Code Review

Present thorough review checking:
- **Bugs**: Edge cases, null checks, error handling, race conditions
- **Security**: Input validation, injection risks, auth issues
- **Performance**: Unnecessary work, memory leaks, N+1 queries
- **Design**: SOLID principles, separation of concerns, testability

Provide: Summary, specific issues with file:line references, suggestions.

---

## Step 3: Understanding Quiz

### Research Foundation

This quiz is designed using evidence-based learning science:

- **Testing Effect**: Retrieving information strengthens memory more than passive review
- **Elaborative Interrogation**: "Why/How" questions force deeper processing and schema building
- **Bloom's Taxonomy**: Progress through cognitive levels from understanding → analysis → evaluation → transfer
- **Mental Model Building**: Help develop expert-like representations with hierarchical structure, pattern recognition, and goal mapping
- **Desirable Difficulties**: Effortful retrieval improves long-term retention
- **Self-Explanation Effect**: Translating code to explanations builds comprehension

### Quiz Setup

Ask the user using AskUserQuestion:

"How deep do you want to go?"
- **Quick** (2-3 questions) - Hit the key points
- **Standard** (5 questions) - Solid understanding
- **Deep** (8-10 questions) - Thorough mastery, recommended for complex changes

Suggest depth based on change complexity if they say "you decide."

---

### Question Framework: Bloom's Taxonomy for Code

Progress through these levels, spending more time on higher levels:

#### Level 1: TRACE (Understand)
*"Can you follow what this code does?"*

Questions that test comprehension of the actual execution:
- "Walk me through what happens when [function] is called with [input]"
- "What is the value of [variable] after line X executes?"
- "In what order do these operations occur?"

**Why this matters**: Code tracing is foundational - it must be learned before code writing.

#### Level 2: CONNECT (Apply/Analyze)
*"How does this fit into the bigger picture?"*

Questions that build the mental model of how code connects:
- "What other files/components call this code?"
- "If this function returns an error, what happens to the UI?"
- "Trace the data flow from [user action] to [this code] to [result]"
- "What state does the app need to be in for this code to run?"

**Why this matters**: Experts have "explicit mapping of code to goals" and "connection of knowledge" - novices lack this.

#### Level 3: EXPLAIN (Analyze)
*"Why does this work the way it does?"*

Elaborative interrogation - the most powerful learning technique:
- "WHY did you use [pattern/approach] instead of [alternative]?"
- "WHY is this code located in [this file] rather than [elsewhere]?"
- "HOW does [library/API] work under the hood here?"
- "WHAT trade-off did this design choice make?"

**Why this matters**: Asking "why" forces integration of new info with prior knowledge and builds schemas.

#### Level 4: EVALUATE (Evaluate)
*"Is this good code? How could it be better?"*

Questions that develop critical judgment:
- "What's the weakest part of this implementation?"
- "Does this follow the [relevant principle - SRP, DRY, etc.]? Why or why not?"
- "What edge case could break this?"
- "Is this code easy to test? What makes it easy or hard?"
- "If a new developer read this, what would confuse them?"

**Why this matters**: Evaluation is a higher-order skill that separates experts from novices.

#### Level 5: TRANSFER (Create/Transfer)
*"How would you extend or modify this?"*

Questions that test ability to apply knowledge to new situations:
- "If we needed to add [new feature], what would need to change?"
- "What if [requirement X] changed - how would you modify this?"
- "How would you refactor this to support [new use case]?"
- "If this needed to handle 10x the load, what would break first?"

**Why this matters**: Transfer questions develop the ability to apply learning to new contexts - the ultimate goal.

---

### How to Quiz

**Execution principles based on learning science:**

1. **One question at a time** (don't overwhelm working memory)

2. **Use AskUserQuestion with multiple choice** including:
   - The correct answer
   - 2-3 plausible wrong answers (things a developer might reasonably think)
   - Make wrong answers educational - they should represent common misconceptions

3. **Interleave question types** (don't group all similar questions)
   - Mix Trace → Connect → Explain → Evaluate throughout
   - This is harder but produces better long-term retention

4. **After each answer, provide rich feedback:**
   - If **correct**: Reinforce WHY, connect to broader principles, praise the reasoning
   - If **incorrect**: Don't just give the answer - EXPLAIN it:
     - Trace through the code showing why the correct answer is right
     - Explain the misconception that led to the wrong answer
     - Connect to the codebase: "This matters because..."

5. **Build progressively** within a session:
   - Start with Trace/Connect (foundation)
   - Move to Explain/Evaluate (deeper)
   - End with Transfer (synthesis)

6. **Encourage self-explanation**:
   - For complex questions, ask them to explain their reasoning
   - "Why do you think that?" before revealing if correct/incorrect
   - Translation exercise: "Explain in plain English what line X does"

---

### Question Generation Guidelines

When generating questions, ensure they are:

1. **Specific to the actual changes** - Reference real file names, function names, variables
2. **Connected to the codebase** - Ask about how changes interact with existing code
3. **Progressively harder** - Build from comprehension to evaluation
4. **Educational even if wrong** - Wrong answers should teach something
5. **Practical** - Focus on things that matter for maintaining this code

**Bad question**: "What design pattern is this?"
**Good question**: "Your `AuthChecker` uses Riverpod's `.when()` pattern. What happens to the UI if `authStateChangesProvider` emits an error?"

**Bad question**: "Is this code good?"
**Good question**: "The `_handleStartSession` function does permission checking, state management, and navigation. Does this violate Single Responsibility? What's the trade-off of keeping vs splitting it?"

---

### Post-Quiz Summary

After all questions, provide:

1. **Score and patterns**: What they got right/wrong, any patterns in mistakes
2. **Mental model reinforcement**:
   - "Here's how this feature fits into the app architecture..."
   - Draw connections between different parts they were quizzed on
3. **Key insights**: The 2-3 most important things to remember about these changes
4. **Further exploration**: Areas of the codebase to explore to deepen understanding
5. **Spaced repetition hook**: "Next time you're in this area of the code, try to recall [X]"

---

## Step 4: Commit Message

Generate concise commit message:
- Imperative mood: "Add", "Fix", "Update"
- Max 50 chars first line
- Specific but concise

Present to user. They commit manually.

## Step 5: Documentation (Optional)

Ask if they want to push docs to Confluence.

If yes:
1. Ask which space/page
2. Ask what problem this solves
3. Write docs:

**Problem:** [1-2 sentences]
**Solution:** [1-2 sentences]

## Overview
[Brief description]

## How It Works
[Key functionality + code paths]

## Usage
[Example code or steps]

## Notes
[Edge cases, limitations]

4. Show draft for approval
5. Push to Atlassian
