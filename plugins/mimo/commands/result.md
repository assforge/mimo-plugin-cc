---
description: Show the final output for a finished MiMo job
argument-hint: "[job-id] [--json]"
allowed-tools: Bash(node:*)
---

Show MiMo job result through the companion script.

Raw slash-command arguments:
`$ARGUMENTS`

Run:
```bash
node "${CLAUDE_PLUGIN_ROOT}/scripts/mimo-companion.mjs" result $ARGUMENTS
```

Return the command stdout verbatim. Do not paraphrase or add commentary.
