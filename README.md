# tools

Personal utility scripts for WSL development.

## new-chat

Launcher for isolated VS Code windows with repo/scratch selection.

Files:
- `bin/new-chat`
- `config/new-chat-settings.json`

Usage:
- `new-chat`
- `new-chat --repo codex`
- `new-chat --scratch`
- `new-chat --shared-instance`

Install options:
1. Add `/home/rhouston/library/repositories/tools/bin` to `PATH`.
2. Or symlink: `ln -sf /home/rhouston/library/repositories/tools/bin/new-chat ~/.local/bin/new-chat`.

Optional env var:
- `NEW_CHAT_SETTINGS_FILE=/path/to/settings.json`
- `NEW_CHAT_CODE_BIN=/path/to/code` (force a specific VS Code launcher)
- `NEW_CHAT_FORCE_WORKSPACE=1` (open a `.code-workspace` wrapper instead of the folder directly)

## Discord repo updates (commits/PRs)

This repo includes `.github/workflows/discord-repo-updates.yml`, which posts updates to Discord on:
- `push`
- `pull_request` (`opened`, `reopened`, `synchronize`, `closed`)
- manual run via `workflow_dispatch`

### Reusable installer for new repos

Use `bin/install-discord-repo-updates` to install the same workflow into any git repo:

```bash
./bin/install-discord-repo-updates --repo /path/to/target-repo
```

Use a different emoji if needed:

```bash
./bin/install-discord-repo-updates --repo /path/to/target-repo --emoji "⚙️"
```

The installer writes:
- `.github/workflows/discord-repo-updates.yml`
- `docs/discord-repo-updates-setup.md`

Template sources live in:
- `templates/discord-repo-updates/.github/workflows/discord-repo-updates.yml`
- `templates/discord-repo-updates/docs/discord-repo-updates-setup.md`

### Discord setup

1. In your Discord server, open `Server Settings` -> `Integrations` -> `Webhooks`.
2. Create a webhook for your target channel (for example `#repo-updates`).
3. Copy the webhook URL.

### GitHub setup

1. In GitHub, go to this repo: `Settings` -> `Secrets and variables` -> `Actions`.
2. Add repository secret:
   - `DISCORD_REPO_UPDATES_WEBHOOK_URL` = the webhook URL from Discord.

The workflow uses Unicode emoji in the commit message template (`🛠️` by default via the installer).

### Test it

1. Go to `Actions` -> `Discord Repo Updates`.
2. Click `Run workflow`, optionally provide `test_message`, and run.
3. Confirm the message appears in the Discord channel.
4. Push a commit to `main` to verify commit notifications.
