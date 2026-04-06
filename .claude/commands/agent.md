---
model: sonnet
---

Design Hanuman agent with controlled loop constraints.

Return JSON:

{
  "role": "string",
  "inputs": ["string"],
  "outputs": ["string"],
  "loop": ["observe", "plan", "act", "evaluate"],
  "constraints": {
    "maxSteps": 6,
    "retryLimit": 2,
    "stopOnStagnation": true,
    "ollamaBackend": "http://localhost:11434"
  },
  "memory": "local-only",
  "safety": ["command-allowlist", "filesystem-scope-restriction"]
}

Rules:
- modular, reusable components
- strict agent loop: observe → plan → act → evaluate
- max 6 steps, max 2 retries, detect stagnation
- local memory only (no external storage)
- enforce safety constraints
- all LLM calls via ollama routing (no external APIs)