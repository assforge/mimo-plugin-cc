# MiMo Plugin for Claude Code

> **Attribution**: This plugin's structure and companion script architecture are based on [openai/codex-plugin-cc](https://github.com/openai/codex-plugin-cc) — the official Codex plugin for Claude Code. We adapted it to work with [MiMo Code](https://mimo.xiaomi.com) (Xiaomi MiMo) instead of OpenAI Codex. Validation logic (`binaryAvailable`, `getMimoAvailability`, `getMimoAuthStatus`) is ported from Codex's `process.mjs` and `codex.mjs`.

Use MiMo Code from inside Claude Code for code reviews or to delegate tasks.

## What You Get

- `/mimo:review` for a read-only MiMo code review
- `/mimo:rescue` to delegate work to MiMo
- `/mimo:status`, `/mimo:result`, `/mimo:cancel` to manage background jobs
- `/mimo:setup` to check MiMo availability

## Requirements

- **MiMo CLI installed** (`npm install -g mimocode` or `curl -fsSL https://mimo.xiaomi.com/install.sh | sh`)
- **Node.js 18.18 or later**

## Install

Add the marketplace in Claude Code:

```
/plugin marketplace add /Users/chomin/Documents/Source/mimo-plugin-cc
```

Install the plugin:

```
/plugin install mimo@mimo-code
```

Reload plugins:

```
/reload-plugins
```

Then run:

```
/mimo:setup
```

## Usage

### `/mimo:review`

Run a MiMo code review on your current work.

```
/mimo:review
/mimo:review --base main
/mimo:review --background
```

### `/mimo:rescue`

Delegate a task to MiMo.

```
/mimo:rescue investigate why the tests are failing
/mimo:rescue fix the failing test
/mimo:rescue --background investigate the regression
/mimo:rescue --model xiaomi/mimo-v2.5-pro fix the bug
```

### `/mimo:status`

Show running and recent MiMo jobs.

```
/mimo:status
/mimo:status task-abc123
```

### `/mimo:result`

Show the final output for a finished job.

```
/mimo:result
/mimo:result task-abc123
```

### `/mimo:cancel`

Cancel an active background MiMo job.

```
/mimo:cancel
/mimo:cancel task-abc123
```

### `/mimo:setup`

Check whether MiMo CLI is installed and authenticated.

```
/mimo:setup
```

## Typical Flows

### Review Before Shipping

```
/mimo:review
```

### Hand A Problem To MiMo

```
/mimo:rescue investigate why the build is failing in CI
```

### Start Something Long-Running

```
/mimo:rescue --background investigate the flaky test
```

Then check in with:

```
/mimo:status
/mimo:result
```

## Architecture

```
plugins/mimo/
├── agents/
│   └── mimo-rescue.md          # Subagent definition
├── commands/
│   ├── review.md               # /mimo:review
│   ├── rescue.md               # /mimo:rescue
│   ├── status.md               # /mimo:status
│   ├── result.md               # /mimo:result
│   ├── cancel.md               # /mimo:cancel
│   └── setup.md                # /mimo:setup
├── scripts/
│   └── mimo-companion.mjs      # Bridge to mimo CLI
└── skills/
    └── mimo-cli-runtime/       # MiMo CLI knowledge
```

## License

MIT
