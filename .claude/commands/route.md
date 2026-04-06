---
model: sonnet
---

Design routing strategy for Hanuman.

Return JSON:

{
  "strategy": {
    "routing": {
      "planning": "deepseek",
      "execution": "llama3:8b",
      "coding": "deepseek-coder"
    },
    "backend": "ollama",
    "baseUrl": "http://localhost:11434",
    "rules": [
      "NO external API fallbacks",
      "routing is explicit and deterministic",
      "model selection based on task type only"
    ]
  }
}

Rules:
- no external APIs under any condition
- explicit routing only (no implicit selection)
- local ollama is the only backend