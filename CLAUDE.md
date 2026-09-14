# CLAUDE.md

@AGENTS.md

## Claude Code additions

These add to AGENTS.md. They do not replace it.

### Privacy

`.claude/settings.json` switches off Claude features that store or send project data outside this folder. The full list is in `context/rules/privacy.md`. Do not loosen these settings. If a task seems to need one, explain why and let the owner decide.

- **Memory.** Auto memory is off. Never write to `~/.claude/projects/.../memory/`. Save memories in `context/memory/`, following `context/memory/README.md`.
- **Temporary files.** Use `context/data/tmp/` instead of the scratchpad or system temp folders.
- **Plans.** Plan files are saved to `context/history/plans/`.
- **Features not to use.** Artifacts, claude.ai connectors (Gmail, Google Drive, Google Calendar, Figma and any others), push notifications, Remote Control, cloud sessions, scheduled cloud routines, subagents with remote isolation, and `/code-review ultra`. Each of them stores data in the Claude account or sends it off this computer.
- **Web.** Ask before using WebFetch or WebSearch. Never put account numbers, balances, positions or personal details in a query or URL.

### Git

- The remote `origin` is GitHub. Never push without the owner's explicit approval for that push.
- Git ignores the contents of `context/data/`, `context/history/`, `context/memory/` and every `.env` file, so they are never pushed. Never force-add them.
- This drive does not record file ownership, so git refuses to run by default. Use `git -c safe.directory=F:/matrix/trade <command>`.

### MCP servers

Claude Code only reads project MCP servers from `.mcp.json` at the repository root. Add a server there only after it is approved in `context/connections/registry.md`. Reference secrets as `${VAR_NAME}` and never write a key into `.mcp.json`.

### Environment

Windows 11. Git Bash and PowerShell are both available.
