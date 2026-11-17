# Neblex Integration Fabric

Connects Antigravity to [Neblex Integration Fabric](https://www.neblex.com/integration-fabric), an integration platform (iPaaS), through the hosted Neblex MCP server. The agent works under the same permissions as your own Neblex account.

## What it does

- Build and test integration flows and AI agents from a prompt, across 300+ connectors including Salesforce, HubSpot, NetSuite, SAP S/4HANA, Snowflake and PostgreSQL
- Open a failed run and show the step and the record it broke on
- Add data quality steps such as deduplication and validation to a flow
- Check which flows failed or stopped running

## Sign-in and permissions

- OAuth 2.1 with PKCE. On first use, Antigravity opens the Neblex sign-in in your browser. Sign in with your second factor and choose the scopes on the consent screen: `operate` (run and observe flows), `author` (build), `publish` (promote, with browser approval).
- Secrets are never returned by any tool. When a connection needs credentials, you enter them in Neblex.
- Publishing into a protected environment waits for a person's approval.

## What you need

A Neblex account. The MCP server is included on every plan, including the free Starter plan: [sign up](https://www.neblex.com/signup).

## Support

community@neblex.com · [Setup guide](https://www.neblex.com/integration-fabric/docs/guide/mcp)
