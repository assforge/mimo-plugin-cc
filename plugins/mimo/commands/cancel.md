---
description: Cancel an active background MiMo job
argument-hint: "[job-id]"
allowed-tools: Bash(node:*)
---

Cancel a MiMo job through the companion script.

Raw slash-command arguments:
`$ARGUMENTS`

Run:
```bash
node "${CLAUDE_PLUGIN_ROOT}/scripts/mimo-companion.mjs" cancel $ARGUMENTS
```

Return the command stdout verbatim. Do not paraphrase or add commentary.
