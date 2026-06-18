---
description: Check whether MiMo CLI is installed and authenticated
argument-hint: ""
allowed-tools: Bash(node:*), AskUserQuestion
---

Check MiMo availability through the companion script.

Run:
```bash
node "${CLAUDE_PLUGIN_ROOT}/scripts/mimo-companion.mjs" setup
```

Return the command stdout verbatim. Do not paraphrase or add commentary.

If MiMo is not found, tell the user to install it:
```bash
npm install -g mimocode
```

If MiMo is found but not authenticated, tell the user to run:
```bash
mimo providers
```
