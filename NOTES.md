# Project wiring notes

- **MCP server:** The project-scoped filesystem server is limited to `docs/` and started with `--read-only`. The only allowed MCP tool is `mcp__filesystem__read_file`, so Claude can inspect API references without granting write or broader filesystem tools.
- **Skill:** `adding-api-routes` captures this project's route, store, validation, error, test, and API-doc conventions. Its description names the new-route/resource task and excludes unrelated work and edits limited to existing routes.
- **Command:** `/review-api` checks API changes against the project checklist without modifying files. `$ARGUMENTS` allows an optional review focus.
- **Hook:** A `PostToolUse` hook matches `Edit|Write` and runs `npm test` after edits, reacting to changes rather than preventing a tool call.
- **Headless task:** The intended bounded task is to summarize `docs/api.md` using `claude -p` with only `Read(docs/api.md)` allowed. I could not run it here: neither the `claude` CLI nor Node/npm is available in this environment. For the same reason, I could not launch the MCP server through `npx`, confirm skill/command triggering, or trigger the hook; those checks remain to be done in a Claude Code environment with the project dependencies installed.
