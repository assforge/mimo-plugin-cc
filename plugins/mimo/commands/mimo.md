---
description: Run a MiMo command or show setup status
argument-hint: "[setup|review|rescue|status|result|cancel] [arguments]"
allowed-tools: Bash(node:*)
---

Route a MiMo request through the companion script.

Raw slash-command arguments:
`$ARGUMENTS`

Routing rules:
- If no arguments are provided, run `setup`.
- If the first argument is one of `setup`, `review`, `rescue`, `status`, `result`, or `cancel`, run that companion command with the remaining arguments.
- Otherwise, treat the full argument string as a `rescue` request.

Run exactly one command:
```bash
node "${CLAUDE_PLUGIN_ROOT}/scripts/mimo-companion.mjs" <resolved-command> <resolved-arguments>
```

Return the command stdout verbatim. Do not paraphrase or add commentary.
