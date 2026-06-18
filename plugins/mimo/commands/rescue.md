---
description: Delegate investigation, a fix request, or follow-up work to MiMo
argument-hint: "[--background|--wait] [--model <model>] [what MiMo should investigate, solve, or continue]"
allowed-tools: Bash(node:*), AskUserQuestion, Agent
---

Invoke the `mimo:mimo-rescue` subagent via the `Agent` tool (`subagent_type: "mimo:mimo-rescue"`), forwarding the raw user request as the prompt.

Raw user request:
$ARGUMENTS

Execution mode:

- If the request includes `--background`, run the subagent in the background.
- If the request includes `--wait`, run the subagent in the foreground.
- If neither flag is present, default to foreground.
- `--background` and `--wait` are execution flags for Claude Code. Do not forward them to the subagent, and do not treat them as part of the natural-language task text.
- `--model` is a runtime-selection flag. Preserve it for the forwarded call, but do not treat it as part of the natural-language task text.

Operating rules:

- The subagent is a thin forwarder only. It should use one `Bash` call to invoke `node "${CLAUDE_PLUGIN_ROOT}/scripts/mimo-companion.mjs" rescue ...` and return that command's stdout as-is.
- Return the MiMo output verbatim to the user.
- Do not paraphrase, summarize, rewrite, or add commentary before or after it.
- If MiMo is missing or unauthenticated, stop and tell the user to run `/mimo:setup`.
- If the user did not supply a request, ask what MiMo should investigate or fix.
