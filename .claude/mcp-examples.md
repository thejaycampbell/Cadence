# MCP Configuration Examples

Copy the relevant block into `.claude/settings.json` under `"mcpServers"` to enable each integration.
The `/onboard` command will guide you through which ones to add and where to get each API key.

---

## Notion

```json
"notion": {
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-notion"],
  "env": {
    "NOTION_API_KEY": "your_integration_secret_here"
  }
}
```

Get key: notion.so/my-integrations → New Integration → copy Internal Integration Secret

---

## Gmail + Google Calendar

```json
"google": {
  "command": "npx",
  "args": ["-y", "@gongrzhe/server-gmail-mcp"],
  "env": {
    "GOOGLE_CLIENT_ID": "your_client_id",
    "GOOGLE_CLIENT_SECRET": "your_client_secret",
    "GOOGLE_REFRESH_TOKEN": "your_refresh_token"
  }
}
```

Get credentials: console.cloud.google.com → Create project → Enable Gmail + Calendar APIs → OAuth credentials

---

## Slack

```json
"slack": {
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-slack"],
  "env": {
    "SLACK_BOT_TOKEN": "xoxb-your-token-here"
  }
}
```

Get token: api.slack.com/apps → Create App → OAuth & Permissions → Install to workspace → copy Bot User OAuth Token
Scopes needed: channels:read, chat:write, im:read

---

## Linear (task/project tracking)

```json
"linear": {
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-linear"],
  "env": {
    "LINEAR_API_KEY": "your_api_key_here"
  }
}
```

Get key: linear.app → Settings → API → Personal API Keys

---

## Brave Search (web research)

```json
"brave-search": {
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-brave-search"],
  "env": {
    "BRAVE_API_KEY": "your_api_key_here"
  }
}
```

Get key: brave.com/search/api → sign up for free tier (2,000 queries/month free)

---

## How to add to settings.json

Open `.claude/settings.json` and add your chosen MCP inside `"mcpServers"`:

```json
{
  "enabledPlugins": {
    "claude-mem@thedotmack": true
  },
  "mcpServers": {
    "github": { ... existing ... },
    "notion": { ... paste from above ... }
  }
}
```

Restart Claude Code after editing settings.json.
