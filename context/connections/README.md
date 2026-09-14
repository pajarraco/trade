# Connections

APIs and MCP servers the agent may use. Nothing is contacted until it is marked `approved` in [registry.md](registry.md).

## Layout

| Path | What goes in it |
|---|---|
| `registry.md` | Every connection, its purpose, the data it sends and its status |
| `.env.example` | Names of the secrets each connection needs, without values. Tracked by git. |
| `.env` | The real secret values. Ignored by git. Create it by copying `.env.example`. |
| `apis/<name>/` | Setup notes and config for one API |
| `mcp/<name>/` | Setup notes, config and any locally installed code for one MCP server |
| `.mcp.json` at the project root | MCP server definitions. Claude Code only reads this file from the root. |

## Adding a connection

1. **Propose.** The agent adds a row to `registry.md` with status `proposed`. The row lists the purpose, the data sent and received, where it runs and which secrets it needs.
2. **Approve.** The owner changes the status to `approved` and logs it in `context/permissions/changelog.md`.
3. **Add secrets.** Put the key names in `.env.example` and the values in `.env`. Never put a secret in code, `.mcp.json`, settings files, records or chat.
4. **Configure.** For an API, write notes and config in `apis/<name>/`. For an MCP server, write notes in `mcp/<name>/` and add the server to the root `.mcp.json`, referencing secrets as `${VAR_NAME}`.
5. **Test** with a paper or demo account and read-only access first. Note the result in the registry.

## Choosing connections

- Start with paper or demo accounts. Use read-only API keys wherever the service offers them.
- Prefer MCP servers that run on this computer over hosted ones. A hosted MCP server receives everything the agent sends it.
- Read the provider's data retention terms before approving, and note them in the registry.
- Only install MCP servers from sources you trust. A local server can run any code on this computer.

## Secrets for MCP servers

Claude Code fills `${VAR_NAME}` placeholders in `.mcp.json` from environment variables. It does not read `.env` files on its own. How to load `context/connections/.env` into the environment gets decided when the first MCP server is added, and is recorded here.
