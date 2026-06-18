---
description: Show running and recent MiMo jobs
argument-hint: "[job-id] [--all] [--json]"
allowed-tools: Bash(node:*)
---

Show MiMo job status through the companion script.

Raw slash-command arguments:
`$ARGUMENTS`

Run:
```bash
node "${CLAUDE_PLUGIN_ROOT}/scripts/mimo-companion.mjs" status $ARGUMENTS
```

Return the command stdout verbatim. Do not paraphrase or add commentary.
