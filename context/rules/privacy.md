# Privacy and data location

status: approved (owner instruction, 2026-09-14)

## The rule

All project data, permissions, history and connection settings stay in this folder. Nothing is sent or saved anywhere else unless the owner agrees first. Nothing is saved to the owner's Claude account.

## What the agent does

- Saves every file inside this folder, and uses `context/data/tmp/` for temporary files.
- Contacts only services approved in `context/connections/registry.md`, and sends them only the data listed there.
- Asks the owner before anything else that sends data off this computer, including web searches, web page fetches, git push, emails and messages.
- Keeps account numbers, balances, positions and personal details out of web searches, URLs and commit messages.
- Tells the owner when a task would need data to leave this folder, and waits for an answer.

## What still leaves this folder

Project settings cannot prevent these. The owner decides whether to accept or change each one.

| What | Where it goes | How to limit it |
|---|---|---|
| The conversation, including every file and API response the agent reads | Anthropic's API, so the model can respond | Check the privacy settings in your Claude account, including whether chats may be used to improve models. |
| Session transcripts | `C:\Users\ernes\.claude\projects\f--matrix-trade\` on this computer, deleted after 30 days by default | Interactive sessions cannot switch transcripts off. Setting the `CLAUDE_CONFIG_DIR` environment variable before starting Claude Code moves all Claude Code storage, including your login, to a folder you choose. |
| Claude Code's own state, such as folder trust and MCP approvals | `C:\Users\ernes\.claude.json` on this computer | Moves with `CLAUDE_CONFIG_DIR`. |
| Data sent to approved connections | The broker or data provider | Only approved services, and only the data listed in the registry. |
| Files pushed to GitHub | The `origin` remote on github.com | Every push needs approval. Git ignores data, history, memory and secrets. |

## Switched off in `.claude/settings.json`

- Auto memory and background memory consolidation
- File checkpoints, which copy edited files to the home folder. `/rewind` can no longer restore file changes, so use git for that.
- Saved prompt history
- Artifacts
- claude.ai connectors such as Gmail, Google Drive, Google Calendar and Figma
- Session upload to claude.ai, Remote Control and mobile push notifications
- Feedback drafts, feedback surveys, `/bug` and `/feedback`
- Telemetry and error reporting

Plan files are saved to `context/history/plans/` instead of the home folder.

## Permission rules in `.claude/settings.json`

- **Blocked.** Artifact tools, claude.ai connector tools, remote triggers, push notifications, scheduled cloud routines, edits under `~/.claude/projects/`, and file-tool reads outside this folder.
- **Ask first.** Web fetch, web search, git push, the GitHub CLI, curl, wget, ssh, scp, rsync and PowerShell web requests.

Settings take effect the next time Claude Code starts in this folder.
