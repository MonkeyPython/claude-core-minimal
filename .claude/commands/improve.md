---
model: sonnet
---

Improve Claude setup.

Scope:
- commands
- context
- settings

Return JSON:

{
  "changes": [
    {
      "file": "string",
      "action": "update | add | remove",
      "reason": "string"
    }
  ]
}

Rules:
- minimal changes only
- no overengineering
- preserve simplicity
- no explanations