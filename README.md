# pi-llm-usage

A [pi](https://github.com/badlogic/pi-mono) extension to view your Anthropic and OpenAI Codex subscription usage as an overlay panel via a single `/usage` slash command.

![pi-llm-usage overlay](./screenshot.png)

## What it does

Type `/usage` in pi to see a quick overlay showing:

- **Anthropic** — 5h session, weekly, and per-model (Opus/Sonnet) usage windows
- **OpenAI Codex** — Session and weekly usage windows

Usage data is fetched from the provider APIs using your existing OAuth credentials.

## Install

Add to your pi settings (`~/.pi/agent/settings.json`):

```json
{
  "packages": ["/absolute/path/to/pi-llm-usage"]
}
```

Or install from Git:

```json
{
  "packages": ["git:github.com/<owner>/pi-llm-usage"]
}
```

## Requirements

- [pi](https://github.com/badlogic/pi-mono) coding agent
- OAuth login for Anthropic and/or OpenAI Codex (via `/login` in pi)

The extension reads OAuth tokens from:
- `~/.pi/agent/auth.json` (pi's OAuth credentials)
- `~/.codex/auth.json` (Codex CLI credentials, fallback for OpenAI)

No API keys needed — it uses your existing OAuth session.

## Usage

```
/usage
```

Press `Esc`, `Enter`, or `q` to close the panel.

## How it works

- **Anthropic**: `GET https://api.anthropic.com/api/oauth/usage` with `anthropic-beta: oauth-2025-04-20` header
- **OpenAI Codex**: `GET https://chatgpt.com/backend-api/wham/usage` with OAuth bearer token

Credit to [CodexBar](https://github.com/steipete/CodexBar) for documenting these endpoints.

## License

MIT
