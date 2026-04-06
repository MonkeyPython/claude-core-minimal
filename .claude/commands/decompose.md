---
model: sonnet
---

Decompose the user's prompt into the smallest independent slash commands that preserve full coherence and functionality.

Rules:
- each command must be self-contained and executable
- no command should depend on output from another unless strictly necessary
- mark dependencies explicitly when unavoidable
- prefer parallel execution over sequential
- do not split if splitting breaks coherence or functionality
- use only commands available in this project

Available commands and their assigned models:
- /explain  [haiku]  — understand code
- /debug    [haiku]  — find root cause
- /review   [haiku]  — code quality issues
- /commit   [haiku]  — analyze and commit changes
- /docs     [haiku]  — update documentation
- /refactor [sonnet] — improve structure
- /test     [sonnet] — generate tests
- /eval     [sonnet] — design evaluation
- /memory   [sonnet] — design memory system
- /tool     [sonnet] — design tool
- /agent    [sonnet] — design agent
- /planner  [sonnet] — plan task
- /route    [sonnet] — design routing strategy
- /improve  [sonnet] — improve Claude setup

Return JSON:

{
  "commands": [
    {
      "order": number,
      "command": "/command-name",
      "model": "haiku | sonnet",
      "prompt": "specific prompt for this command",
      "depends_on": [order] | [],
      "can_parallelize": boolean
    }
  ],
  "summary": "one-line explanation of decomposition strategy"
}

After returning JSON, ask the user: "Execute these commands? (yes / edit / no)"

If confirmed, execute each command in order respecting dependencies.
Parallel commands (can_parallelize: true, no shared dependencies) run together.
