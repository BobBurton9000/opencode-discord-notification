# opencode-discord-notification

OpenCode plugin that sends Discord webhook notifications on session completion and permission requests.

## Features

- ✅ **Completion Notifications** — Green embed when a session goes idle (minimum 5 min).
- ⚠️ **Permission Alerts** — Orange embed when OpenCode is blocked waiting for approval, including the blocked command.
- 🔒 **Privacy-First** — Assistant response content is never sent to Discord; only metadata.
- 📊 **Context Stats** — Context window usage % and total token count.
- 🤖 **Model Info** — Which model was used.
- ⏱️ **Session Duration** — How long the session ran, shown in the embed footer.
- 🚫 **Sub-Session Filtering** — Child sessions (with a `parentID`) are ignored.

## Installation

```json
{ "plugin": ["bobs-opencode-discord-notifier@0.1.7"] }
```

## Configuration

Two sources, checked in priority order:

### 1. In `opencode.json` (preferred)

```json
{
  "plugin": ["bobs-opencode-discord-notifier@0.1.7"],
  "discordNotifications": {
    "enabled": true,
    "webhookUrl": "https://discord.com/api/webhooks/...",
    "username": "OpenCode Notifier",
    "avatarUrl": "https://opencode.ai/logo.png"
  }
}
```

### 2. Config file fallback

`~/.config/opencode/discord-notification-config.json`:

```json
{
  "enabled": true,
  "webhookUrl": "https://discord.com/api/webhooks/...",
  "username": "OpenCode Notifier",
  "avatarUrl": "https://opencode.ai/logo.png"
}
```

| Field | Required | Default |
|---|---|---|
| `webhookUrl` | Yes | — |
| `enabled` | Yes | — |
| `username` | No | `OpenCode Notifier` |
| `avatarUrl` | No | None |

## Behavior

| Event | Embed Color | Min Duration |
|---|---|---|
| `session.idle` | Green | 5 minutes |
| `permission.asked` | Orange | None (immediate) |

Idle notifications are only sent for sessions that ran at least 5 minutes. Sub-sessions spawned by tools are always skipped.

Each embed includes: title, context usage %, total tokens, model name, session ID, and duration.

## Development

```bash
npm install
npm run build && npx tsc
```

## License

MIT
