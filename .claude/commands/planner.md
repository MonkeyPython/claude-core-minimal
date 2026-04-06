---
model: sonnet
---

Plan task using Hanuman planner (deepseek model).

Return JSON:

{
  "steps": ["string"],
  "dependencies": ["string"],
  "model": "deepseek",
  "constraints": {
    "maxSteps": 6,
    "retryLimit": 2,
    "stopOnStagnation": true
  }
}

Rules:
- minimal, ordered steps
- prompts for small local models (short, deterministic, action-oriented)
- avoid long chain-of-thought reasoning
- all planning via deepseek (ollama localhost:11434)
- no external APIs