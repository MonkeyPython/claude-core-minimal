# claude-core-minimal

Minimal base repository for Claude Code projects. Provides a opinionated `.claude/` setup focused on low-noise, cost-efficient usage.

## What's included

```
.claude/
├── settings.json          # Global behavior (temperature, token limits, rules)
├── commands/              # Slash commands
│   ├── commit.md          # /commit  — analyze changes, return structured JSON
│   ├── debug.md           # /debug   — find root cause and fix
│   ├── docs.md            # /docs    — update documentation
│   ├── explain.md         # /explain — concise code explanation (default)
│   ├── refactor.md        # /refactor — clean up code, return only code
│   ├── review.md          # /review  — structured issue report in JSON
│   └── test.md            # /test    — generate tests, no explanations
└── context/
    ├── conventions.md     # Coding conventions injected into every session
    └── project.md         # Project goals and context
```

## Settings

[settings.json](.claude/settings.json) configures Claude's behavior globally:

| Key | Value | Purpose |
|---|---|---|
| `defaultCommand` | `explain` | Command run when no slash command is specified |
| `temperature` | `0.2` | Low randomness for deterministic outputs |
| `maxTokens` | `4096` | Token cap per response |
| `rules` | see file | Behavioral constraints applied to every prompt |

## Slash commands

| Command | Output | Use case |
|---|---|---|
| `/commit` | JSON | Propose commits from staged changes |
| `/debug` | cause + fix | Find root cause of a bug |
| `/docs` | markdown | Update documentation to match code |
| `/explain` | prose | Explain selected code briefly |
| `/refactor` | code only | Improve readability, reduce complexity |
| `/review` | JSON | Flag bugs, edge cases, maintainability issues |
| `/test` | code only | Generate tests for selected code |

## Usage

Clone and use as a starting point for any project:

```bash
git clone https://github.com/jlgut/claude-core-minimal
cp -r claude-core-minimal/.claude your-project/
```

Then customize [context/project.md](.claude/context/project.md) and [context/conventions.md](.claude/context/conventions.md) for your project.

## Design goals

- **Fast iteration** — commands return structured output with no filler
- **Low noise** — no co-authored-by tags, no explanations unless asked
- **Cost-efficient** — low temperature + token cap keeps sessions focused
