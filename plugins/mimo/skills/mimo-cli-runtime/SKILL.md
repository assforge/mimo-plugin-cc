---
name: mimo-cli-runtime
description: MiMo CLI runtime knowledge — how to invoke mimo run, manage sessions, and handle output
---

# MiMo CLI Runtime

## Core command

```bash
mimo run [message..]
```

## Key flags

| Flag | Description |
|------|-------------|
| `--dir <path>` | Working directory |
| `--model <model>` | Model to use (e.g., `xiaomi/mimo-v2.5-pro`) |
| `--variant <variant>` | Model variant (reasoning effort) |
| `-s, --session <id>` | Continue a specific session |
| `-c, --continue` | Continue the last session |
| `--fork` | Fork session before continuing |
| `--background` | Run in background |
| `-f, --file <path>` | Attach file(s) |
| `--title <title>` | Session title |
| `--format json` | Output as JSON |

## Session management

```bash
# Continue last session
mimo run -c "continue working"

# Fork a session
mimo run --fork -s <session-id> "new direction"

# List agents
mimo agent list
```

## Output handling

- MiMo outputs to stdout
- Capture with `$(mimo run "task")` or pipe to file
- Use `--format json` for structured output

## Authentication

```bash
mimo providers    # Manage providers/auth
mimo --version    # Check version
```
