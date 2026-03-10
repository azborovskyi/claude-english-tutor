---
description: "Start an English practice session — analyze prompts for mistakes, review patterns, or run targeted drills"
user_invocable: true
---

# English Practice Session

Delegate to the **english-tutor** agent to run a practice session.

## Determine the mode

Based on the user's request (or ask if unclear), pick one of these modes:

### 1. `analyze` — Scan recent prompts
Tell the agent: "Scan my recent prompts from ~/.claude/history.jsonl for grammar mistakes and language patterns. Update the mistake database with any new findings. Show me a summary of what you found."

### 2. `review` — Review my top mistakes
Tell the agent: "Show me my most common English mistakes ranked by frequency. For each one, explain the rule, show my actual examples, and give additional examples in different contexts."

### 3. `drill` — Practice exercises
Tell the agent: "Run me through practice exercises targeting my most frequent mistakes. Present exercises one at a time, evaluate my answers, and explain the correct answer."

If the user specifies a category (e.g., "drill articles"), pass that along.

### 4. `build` — Generate interactive exercise app
Tell the agent: "Build an interactive web exercise app in the project root targeting my top mistake patterns. Use React + TailwindCSS. Make it polished and engaging."

## First-time setup

The english-tutor agent stores its memory at `.claude/agent-memory-local/english-tutor/` (relative to project root). Check for `MEMORY.md` at that path to determine if a prior analysis exists.

If this is the first session (no MEMORY.md exists), always start with `analyze` mode first to build the initial mistake database before doing drills.
