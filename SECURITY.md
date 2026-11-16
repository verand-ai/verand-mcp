# Security

## Reporting a vulnerability

Email **support@verand.ai** with "Security" in the subject line. Please don't open a public issue or discussion for a security report.

Include what you found, the steps to reproduce it, and the endpoint or file involved. We'll acknowledge the report within two business days and keep you updated until it's resolved.

## Scope

- The remote MCP server at `https://app.verand.ai/mcp` and its OAuth sign-in
- The OAuth and MCP metadata documents under `https://app.verand.ai/.well-known/`
- The files in this repository

This repository holds configuration and instructions only (manifests, an MCP server declaration and an agent skill). It contains no executable code and no credentials. The server itself is operated by Verand.

## How access works

- Sign-in is OAuth 2.1 with PKCE. There is no API key and no shared secret in any client configuration.
- Every tool call runs as the signed-in user, with that user's permissions, against their own account's data.
- A user can see and revoke every connected client in Verand, under Settings, Integrations, MCP connections.
- Publishing from an AI assistant and applying fixes to a live site are off until an account owner turns them on, and each one needs the person's approval of the exact text, tied to that text by a short-lived code.
