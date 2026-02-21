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
