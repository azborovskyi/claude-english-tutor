# English Tutor for Claude Code

A Claude Code agent that analyzes your prompt history to find recurring English mistakes, builds a prioritized database of your weak spots, and generates targeted exercises to fix them.

## Why

I use Claude Code a lot for my daily work, and English is not my native language. All my prompts are in English, which means Claude Code already has a massive corpus of my real, unfiltered writing — the kind of text where habitual mistakes show up over and over.

There are hook-based tools that correct your English in real-time as you type prompts. I tried that approach and found it counterproductive: it splits your attention between the task you're actually solving and the language correction. You end up doing both things poorly — the coding task gets interrupted, and the English correction flies by without you actually learning the rule behind it.

I prefer to separate the two activities. During work, I focus on work. Then, in a dedicated practice session, the tutor agent analyzes what I wrote, surfaces the patterns I keep getting wrong, explains the rules, and drills me on them until they stick. This way the learning is intentional and the practice is targeted at my specific weak points — not generic grammar exercises.

## How it works

The agent reads `~/.claude/history.jsonl`, extracts the natural language portions of your prompts, and identifies recurring grammar mistakes and awkward phrasing. It categorizes them, ranks by frequency, and builds exercises targeting your specific weak points.

Your prompt history accumulates automatically as you use Claude Code across all projects — no setup needed to start collecting data.

## Setup

Clone the repo and run Claude Code from it:

```bash
git clone <repo-url> ~/english-tutor
cd ~/english-tutor
claude
```

The agent and skill are defined in `.claude/` and are automatically picked up by Claude Code when you open a session from this directory.

## Usage

Start a practice session:

```
/english-practice
```

### Modes

**Analyze** — scan your recent prompts for new mistakes:
```
/english-practice analyze
```

**Review** — see your top mistake patterns with real examples:
```
/english-practice review
```

**Drill** — practice exercises targeting your weakest areas:
```
/english-practice drill
```

You can also target a specific category:
```
/english-practice drill articles
```

**Build** — generate an interactive web exercise app:
```
/english-practice build
```

## What gets tracked

The agent maintains a local mistake database in `.claude/agent-memory-local/` (gitignored — your data stays private). It includes:

- Mistake categories (articles, prepositions, word order, tense, word choice, etc.)
- Frequency rankings — most common mistakes get priority
- Real examples from your prompts with corrections
- The underlying grammar rules explained simply
- Progress tracking over time

## Mistake categories

The agent groups mistakes into patterns rather than flagging individual typos. Examples:

- **Missing articles** — "I want to add button" → "I want to add **a** button"
- **Preposition errors** — "depends from" → "depends **on**"
- **Word order** — "I want that it works" → "I want **it to work**"
- **Awkward phrasing** — non-idiomatic constructions a native speaker would say differently
- **Word choice** — false friends and near-synonyms used incorrectly

It distinguishes real errors from acceptable informal register — terse prompts to an AI are fine.

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI
- Prompt history in `~/.claude/history.jsonl` (accumulated automatically as you use Claude Code)

## License

MIT
