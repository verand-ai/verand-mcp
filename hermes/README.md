# Verand for Hermes Agent

Connect Hermes to [Verand](https://verand.ai), so it can answer questions about your own website from your real data: what to write next, why rankings or traffic moved, where ChatGPT, Gemini, Google AI Overviews, Google AI Mode, Perplexity and Claude mention and cite you, what's wrong with a page, and whether a draft clears its compliance checks.

Verand writes content for your authority, gets it found on Google and in AI answers, and tracks where you rank and where the answers name you, behind a compliance gate that stops a bad claim publishing.

This package is configuration and Markdown only: a manifest, one MCP server declaration and one skill. No Python, no Desktop code.

## Install

```sh
hermes plugins install verand
hermes plugins enable verand
```

The first time a Verand tool is used, a browser window opens. Sign in to Verand and approve access. There's no API key. You need a Verand account; plans start at $149/month with a 7-day free trial ([pricing](https://verand.ai/pricing)).

## What's in it

- `mcp.json`: one server, `verand`, which runs the pinned `mcp-remote@0.15.2` through `npx` against `https://app.verand.ai/mcp` (Streamable HTTP, OAuth 2.1 with PKCE and dynamic client registration). Node.js 20.18.1 or later is needed. A portable `streamable-http` entry can't request OAuth in Hermes yet, which this server needs.
- `plugin.json`: marks the `verand` server `trust: untrusted`, so Hermes asks before every Verand tool that isn't annotated read-only, and refuses those tools in unattended runs.
- `skills/verand/SKILL.md`: when to reach for Verand, and the order to call it in (`verand_list_sites` first, `verand_get_playbook` for bigger jobs).

## What it can do

- Read your sites, articles, site issues, rankings, Search Console and GA4 data, and AI search visibility per assistant
- Generate drafts, run research and analyses, and open a published page for a refresh. These use your plan's monthly allowance, the same as the dashboard
- Edit a draft, with every check re-run, and propose a fix for a failing check with before-and-after validation
- Save facts about your business to your knowledge base, and update your Brand Hub after showing you the change
- Publish an approved article, or apply a fix from your Issues list to your live pages (up to 10 at a time), only if an account owner has turned that on in Verand, and only after the exact text is shown to you and you say yes

## What it can never do

- Publish an article you haven't approved in the chat, or change a live page in a way you haven't seen
- Override a hard-tier compliance block
- Delete an article, a draft or a page. There's no tool for it

## Disclosure

- **Network:** every tool call goes to Verand's hosted server at `app.verand.ai`, which reads and writes your own Verand account's data, scoped to your sign-in. Sign-in goes through Verand's OAuth server (hosted on Supabase, at `rknxrqatqexzvieekdlo.supabase.co`).
- **Remote tool set:** the tools are served by Verand at runtime, so the pinned commit covers this configuration and the skill, not the tool list. Read-only tools carry `readOnlyHint: true`; every write tool carries `readOnlyHint: false`, and the ones that change something on your live site or override a review-tier compliance flag also carry `destructiveHint: true`.
- **Writes that reach your website:** publishing an article and applying fixes go through your site's own Verand connection (WordPress, or a pull request on GitHub). Both are off until an account owner switches on "Allow AI assistants to publish and apply fixes", and each needs a confirmation code tied to the exact text you approved.
- **Cost:** generating drafts, research and analyses draws on your Verand plan's monthly allowance. There are no overage charges: at the cap, the tool says so and stops.
- **Local process and credentials:** `npx` downloads and runs `mcp-remote@0.15.2`. On first use it opens a localhost callback port and your browser, and stores OAuth tokens under `~/.mcp-auth`. Without a stored token, an unattended run fails at Hermes's connect timeout instead of hanging. No credentials are in this repository.
- No telemetry from the package, no background process beyond the MCP server process Hermes starts, and no self-updater.

Compliance results are researched from the regulators' own text and tested by Verand. Not reviewed by a licensed attorney. Your counsel confirms applicability. Not legal advice.

## Support

- Guide: [The MCP connector](https://verand.ai/help/the-mcp-connector)
- Email: support@verand.ai
- Privacy: https://verand.ai/privacy
