# Verand MCP connector

Connect Claude, ChatGPT, Cursor, VS Code or any MCP client to [Verand](https://verand.ai), so your assistant can read your site's content, health, rankings and AI search visibility, and start work, without opening the dashboard.

Verand writes content for your authority, gets it found on Google and in AI answers (ChatGPT, Gemini, Google AI Overviews, Google AI Mode, Perplexity and Claude), and tracks where you rank and where the answers name you, behind a compliance gate that stops a bad claim publishing.

**Endpoint:** `https://app.verand.ai/mcp` (remote MCP over HTTP, OAuth sign-in, no API key)

## Connect

### Claude

1. Open **Customize → Connectors**
2. Click **+**, then **Add custom connector**
3. Paste `https://app.verand.ai/mcp`
4. Sign in with your Verand account and approve the access it asks for

The free Claude plan allows one custom connector. On Team and Enterprise an Owner may need to add it for the workspace first.

### ChatGPT

Needs a paid plan and the web app.

1. Open **Settings → Security and login** and turn on **Developer mode**
2. Go to connectors, click **+**, and create an app for your MCP server
3. Paste `https://app.verand.ai/mcp` and set authentication to **OAuth**
4. Sign in and approve

### Claude Code

```sh
claude mcp add --transport http verand https://app.verand.ai/mcp
```

Then run `/mcp` inside Claude Code and choose to authenticate.

### Cursor and VS Code

Add this to your MCP config (`~/.cursor/mcp.json` for Cursor):

```json
{ "mcpServers": { "verand": { "url": "https://app.verand.ai/mcp" } } }
```

Reload the window. Your editor opens a browser to sign in.

### Anything else

Any client that supports remote MCP servers over HTTP can connect. Paste the endpoint wherever it asks for a server URL, and choose **OAuth** if it asks how to authenticate.

## What it can do

- Read your sites, articles, site issues, rankings, Search Console and Analytics data, and AI search visibility per engine
- Generate drafts, run analyses and open a published page for refresh. These use your plan's monthly allowance, the same as the dashboard
- Propose a fix for a failing check, with before-and-after validation
- Save facts about your business to your knowledge base

## What it can never do

- Publish anything to your live site
- Override a compliance block
- Delete any of your content

This is by construction, not by policy: there is no publish, override or delete tool for a client to call, so no instruction, mistake or prompt injection can reach one. Approval stays with a person in the dashboard.

## Requirements

A Verand account. The connector is included on every plan. [Start at verand.ai](https://verand.ai).

## Docs and support

- Full guide: [The MCP connector](https://help.verand.ai)
- Questions: open a [discussion](../../discussions) or email support@verand.ai
