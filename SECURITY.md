# Security policy

## Reporting a vulnerability

Please report security issues privately through GitHub: open the **Security** tab of this repository and choose **Report a vulnerability**. Don't open a public issue for a security problem.

Include what you found, how to reproduce it, and the impact you expect. We aim to acknowledge reports within 2 business days and will keep you updated until the issue is resolved.

## Scope

This repository contains only plugin manifests that point AI clients at the hosted Neblex MCP server (`https://if.neblex.com/mcp`). It ships no executable code, scripts or hooks.

Reports about the Neblex MCP server or Neblex Integration Fabric itself are also welcome through the same private channel.

## How the plugin handles access

- Sign-in uses OAuth 2.1 with PKCE. Users authenticate in the browser with a second factor and choose scopes on the consent screen.
- The client acts under the user's own Neblex permissions.
- Connection secrets are never returned by any tool; credentials are entered in Neblex.
- Publishing to protected environments waits for a person's approval.
