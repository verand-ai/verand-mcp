# Verand MCP connector

[![AllMCPs Verified](https://allmcps.com/api/badge/verand)](https://allmcps.com/mcp/verand?verify=73543106-8de3-4d13-a4e5-beea35ea1b9a)

[![Verand MCP connector on AI Agents Listing](https://aiagentslisting.com/verand-mcp-connector/badge.svg?claim=e86ea2452dcb2193740afcb64c5c6aa7)](https://aiagentslisting.com/mcp/verand-mcp-connector)

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

### Zapier

Until the Verand app for Zapier is listed, Zapier's own **MCP Client** app can connect:

1. In Zapier, open **Apps**, click **+ Add connection** and choose **MCP Client**
2. Set **Server URL** to `https://app.verand.ai/mcp`, **Transport** to **Streamable HTTP** and **OAuth** to **Yes**
3. Sign in with your Verand account and approve

Its **Run Tool** action calls one Verand tool per step. Leave **Allow AI assistants to publish and apply fixes** off while a Zap uses the connection: a Zap has no one to show the article or the fix to before it goes live.

### Anything else

Any client that supports remote MCP servers over HTTP can connect. Paste the endpoint wherever it asks for a server URL, and choose **OAuth** if it asks how to authenticate.

## What it can do

- Read your sites, articles, site issues, rankings, Search Console and GA4 data, and AI search visibility per assistant
- Generate drafts, run research and analyses, and open a published page for a refresh. These use your plan's monthly allowance, the same as the dashboard
- Edit a draft the way the editor does, with every check re-run, and propose a fix for a failing check with before-and-after validation
- Save facts about your business to your knowledge base, and update your Brand Hub after showing you the change
- Publish an approved article to your site, or apply a fix from your Issues list to your live pages (up to 10 at a time), but only if an account owner has turned on **Allow AI assistants to publish and apply fixes**, and only after the assistant shows you the exact text and you say yes

## What it can never do

- Publish an article you haven't reviewed and approved in the chat
- Change a live page in a way you haven't seen and approved in the chat
- Override a hard-tier compliance block, or a review-tier flag without the account owner's switch and written reason
- Delete an article, a draft or a page

Publishing and applying fixes are **off** until an account owner switches them on in Verand, under Settings, Integrations, MCP connections. Each approval is tied to the exact text you were shown: if it changes, or 30 minutes pass, the publish is refused and the assistant has to show you the new version. The same compliance gate as the dashboard runs again at the moment of publishing. On a GitHub site, publishing opens a pull request rather than changing the live site.

The last two lines above aren't promises about behaviour. There's no tool that deletes your articles, pages, briefs or knowledge base, and no tool can clear a hard-tier compliance block, so no instruction, mistake or prompt injection can reach one. The only things it can remove are a tracked keyword or a Brand Hub entry, each after you name it and say yes.

Every tool carries MCP annotations (`readOnlyHint`, `destructiveHint`), so clients that ask before write actions will ask before every Verand write.

Compliance results are researched from the regulators' own text and tested by Verand. Not reviewed by a licensed attorney. Your counsel confirms applicability. Not legal advice.

## Requirements

A Verand account. The connector is included on every plan. [Start at verand.ai](https://verand.ai).

## Docs and support

- Full guide: [The MCP connector](https://verand.ai/help/the-mcp-connector)
- Questions: open a [discussion](../../discussions) or email support@verand.ai
- Security reports: see [SECURITY.md](SECURITY.md)
