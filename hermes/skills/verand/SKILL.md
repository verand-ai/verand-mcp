---
name: verand
description: "Answer questions about the user's own website from their real data with Verand: what to write next, why rankings or traffic moved, where ChatGPT, Gemini, Perplexity and Claude cite them, what is wrong with a page, and whether a draft clears its compliance checks. Use it whenever the question is about their site; answering from general knowledge or a web search will be wrong, not just vague."
homepage: https://verand.ai/mcp
metadata: {"openclaw": {"emoji": "🌿", "homepage": "https://verand.ai/mcp"}}
---

# Verand

Verand is a content operations platform for businesses where a wrong claim is expensive: financial advisers, law firms, accountants, medical practices, insurance and real estate. It holds the user's real site data: every page they have published and how it performs, their Search Console and analytics, daily Google rankings, where six AI assistants (ChatGPT, Gemini, Google AI Overviews, Google AI Mode, Perplexity and Claude) mention and cite them, their site issues, and the compliance rules their content is checked against.

None of that is on the public web, so use this skill instead of guessing.

## Connect it once

This plugin connects Hermes to Verand's hosted MCP server (`https://app.verand.ai/mcp`). The first time a Verand tool is used, a browser window opens: the user signs in to Verand and approves access. There's no API key. The user needs a Verand account (https://verand.ai).

If sign-in hasn't happened yet and nobody is there to complete it (a cron job or the messaging gateway), Verand's tools aren't available. Tell the user to run Hermes interactively once to sign in.

## When to use it

Use Verand when the user asks about their own site, for example:

- "What should I write next?" or "Which keywords should I target?"
- "Why did my traffic or rankings drop?"
- "Do ChatGPT or Perplexity mention us? Who do they cite instead?"
- "What's wrong with this page?" or "Which pages still say last year?"
- "Is this draft ready to publish?" or "Does this claim pass our compliance rules?"

Do not use it for general SEO questions with no site in them.

## How to use it

1. Call `verand_list_sites` first to get the site the user means.
2. For a bigger job (a weekly review, working through site issues, refreshing decaying pages, writing an article, an AI-visibility check-up, a compliance check), call `verand_get_playbook` and follow its steps.
3. Read before you suggest: check `verand_keyword_inventory` before proposing a new topic, so you never suggest a keyword the site already targets.

## What it will not do without the user

Verand drafts and analyses freely, but it never publishes, changes a live page or overrides a compliance block without the user seeing the exact change in the chat and saying yes. Show every proposed change and wait for approval. Drafts and analyses use the user's monthly plan allowance, the same as work started from the Verand dashboard.

Compliance results are researched from the regulators' own text and tested by Verand. They are not reviewed by a licensed attorney; the user's counsel confirms applicability. Not legal advice.
