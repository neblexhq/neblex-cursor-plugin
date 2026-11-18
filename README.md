# Neblex plugin for Cursor

Connects Cursor to the hosted Neblex MCP server, so Cursor's agent can build, test and run integrations in [Neblex Integration Fabric](https://www.neblex.com/integration-fabric), an integration platform (iPaaS). The agent works under the same permissions as your own Neblex account.

## What it does:

| Area | Examples |
| --- | --- |
| Discover | Search 300+ connectors, their operations and node types |
| Build | Create and edit flows, forms, internal apps, data tables, data models and AI agents |
| Check | Validate before saving and test before publishing |
| Run | Run granted flows and read results, run history, run events and flow health |
| Connect | Create a connection without secrets and get the link to finish it |
| Version | List versions and restore earlier ones |
| Publish | Take flows, forms, apps and agents live or offline, with approval where required |

## What you need:

- Cursor with plugin support.
- A Neblex account. The free Starter plan includes the full platform and 1,000 executions a month: [sign up](https://www.neblex.com/signup).

## Setup:

1. Install the plugin. The Cursor Marketplace listing is in review; until it's live, install it manually:

   ```bash
   git clone https://github.com/neblexhq/neblex-cursor-plugin.git ~/.cursor/plugins/local/neblex
   ```

   Then reload Cursor (Developer: Reload Window) and check that Neblex appears in Customize.
2. Approve the `neblex` MCP server when Cursor asks.
3. On first use, Cursor opens the Neblex sign-in in your browser. Sign in, choose the scopes and the projects or flows Cursor may reach on the consent screen, and approve.

There is no API key to copy. The plugin only points Cursor at `https://if.neblex.com/mcp` (Streamable HTTP, OAuth).

## Test it:

Ask the agent: "List my Neblex flows." You should see the flows in your workspace. Then try:

- "Build a flow that syncs new HubSpot contacts to Snowflake and removes duplicates first."
- "Why did last night's order sync fail? Show me the step where it stopped."
- "Draft an IT service desk agent that answers from our SOPs and asks before it opens a ticket."
- "Connect our Postgres database and send me the link to enter the password."

## Kimi Code:

The same repository also works as a Kimi Code plugin (`kimi.plugin.json`). In Kimi Code, run:

```text
/plugins install https://github.com/neblexhq/neblex-cursor-plugin
```

Then run `/reload`. On first use, Kimi Code opens the Neblex sign-in in your browser, the same as Cursor.

## Gemini CLI:

The repository is also a Gemini CLI extension (`gemini-extension.json`). Install it with:

```bash
gemini extensions install https://github.com/neblexhq/neblex-cursor-plugin
```

Start Gemini CLI and run `/mcp auth neblex` if it doesn't open the Neblex sign-in on first use.

## Google Antigravity:

The `antigravity/` folder is an Antigravity plugin. Clone the repository, then run:

```bash
agy plugin install ./neblex-cursor-plugin/antigravity
```

On first use, Antigravity opens the Neblex sign-in in your browser.

## Grok Build:

The repository is also a Grok Build plugin (`.grok-plugin/plugin.json` and `.mcp.json`). Install it from the xAI plugin marketplace once listed. On first use, Grok Build opens the Neblex sign-in in your browser.

## Cline and Kilo Code:

Add Neblex as a remote MCP server:

1. Open the MCP Servers settings and choose **Add Remote Server**.
2. Server name `neblex`, server URL `https://if.neblex.com/mcp` (Streamable HTTP).
3. Click **Authenticate** on the new server and sign in to Neblex in your browser.

Or add it to the MCP configuration file directly:

```json
{
  "mcpServers": {
    "neblex": {
      "type": "streamableHttp",
      "url": "https://if.neblex.com/mcp"
    }
  }
}
```

Then ask: "Use the neblex MCP server to list my flows."

## Sign-in and permissions:

- OAuth 2.1 with dynamic client registration. Interactive building uses step-up with an enrolled second factor.
- Scopes you can grant on the consent screen:
  - `operate`: run and observe assigned flows
  - `author`: build flows, apps, forms, data tables, connections and agents
  - `publish`: promote to protected environments (with browser approval)
- Cursor acts under your own permissions and can't do anything your account can't.
- Secrets are never returned to Cursor. When a connection needs credentials, the server creates it without secrets and returns a link where a person enters them in the browser.
- Publishing into a protected environment waits for a person's approval.
- Connected clients are listed, and can be revoked, in Neblex under API Consumers.

## Notes:

- The MCP server is included in every Neblex plan, including the free plan.
- Flows and AI agents run in the cloud or on a single native on-premises runtime inside your network.
- Deduplication, validation and a quarantine for bad records run as steps inside a flow.

## Links:

- [MCP documentation](https://www.neblex.com/integration-fabric/docs/guide/mcp)
- [Neblex MCP server repository](https://github.com/neblexhq/neblex-mcp)
- [Pricing](https://www.neblex.com/integration-fabric/pricing)

## Support:

Open an issue in this repository, or ask Matt, the in-product assistant, inside Neblex.
