# VirtualDesktopCommands

Help-center commands for the Virtual Desktop Discord support bot (unified-bot), one JSON file per command.

## Rules

- Every command lives at `commands/<name>.json`, and the filename (without `.json`) **must equal** the `name` field.
- Names match `^[a-z0-9_-]{1,32}$` (commands and pages).
- Each file must validate against `commands.schema.json` - run `npm run validate` locally; CI enforces it on every push/PR.
- Page names must be unique within a command.

## How edits arrive

- **In-Discord editor** - staff use `/create_command` / `/edit_command` in the guild; the bot commits the changed file here directly.
- **LLM proposals** - the assistant bot submits change proposals to unified-bot's proposals API; staff approve/reject a review card in Discord, and approval commits here.
- **Direct edits/PRs** - fine too; the bot polls this repo and hot-reloads when the `commands/` directory changes.

Conflicts are detected per file via GitHub blob SHAs, so concurrent edits to different commands never collide.
