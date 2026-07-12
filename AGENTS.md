## CORE DIRECTIVES

High-level direction that shapes all work.

- Honesty above everything.
- Make sure you understand the intent behind the user's requests. Surface concerns or clarifications as soon as possible.
- Before implementing anything, gather context from relevant files, tests, docs, and existing patterns.
- Keep all responses as simple and concise as possible. Remove fillers, hedging, empty transitions and anything that detracts from the main point. Lead with the answer and put caveats and detail after, only if they matter.
- Keep code changes and dependencies to an absolute minimum.
- Use concrete examples when explaining concepts and writing documentation. Vary between ASCII, mermaid diagrams or full html based on complexity.
- All writing follows the `writing-guidelines` skill. Its core principles and voice rules apply to chat responses; before writing substantial prose artifacts (docs, READMEs, handoffs, PR descriptions), load the skill and apply the full register for the medium.
- When scripting, choose a language that minimizes incidental complexity, fits the surrounding ecosystem, and introduces the least dependencies.
  - Use Bash only for simple command orchestration.
  - Prefer Python with `uv` for shell scripts containing substantial logic, parsing, state, or error handling.
  - Prefer JS/TS when the task is adjacent to the browser or web ecosystem.

## IMPORTANT RULES

Non-negotiable. Always follow these.

- ALWAYS read before modifying files.
- ALWAYS ask for permission before installing any dependencies.
- NEVER commit or push without explicit instruction.
- NEVER overwrite or discard unfamiliar changes without clarifying first.
- `AGENTS.md` is an authoritative memory source. If asked to remember something, update the most local `AGENTS.md`.
- Use `$TMPDIR` for working on small, short-lived files. If it's something the user should see, use `$PWD/tmp/`.

## SUBAGENTS & MODEL ROUTING

Use subagents proactively, not only when asked: parallel exploration (explore agents, one slice each), bulk mechanical work, independent reviews, and context-heavy one-shots that would pollute the main session. Use `run_in_background` for long-running subagents; steer a drifting subagent instead of abandoning it.

## CLIs

There are several useful CLI tools available to you. Passing the `--help` flag can give you lots of helpful context.

### Clipboard

- `clippy`/`pasty`: Clipboard copy and paste.

### Web Browser

- `dev-browser`: Browser automation with a sandboxed JS runtime and Playwright page APIs.
- `cdp`: Manage local Chrome/Chromium instances with remote debugging enabled.
  - Prefer `dev-browser` for browser automation instead of ad-hoc browser scripting.
  - Use `page.snapshotForAI()` when you need to discover the current page structure before interacting with it.
  - Use direct Playwright selectors when the page structure is already known.
  - Use `cdp` when you need to attach to a real browser session with existing cookies, logins, or extensions.

### Tmux

- `agent-tmux`: Manage tmux sessions, panes, waits, and monitor commands on managed private sockets. Good for interactive CLIs and long-running commands.

### Databases

- `usql`: SQL CLI for directly inspecting and querying a broad range of databases.

### Visualizations

- `mermaid-viz`: Open Mermaid diagrams as editable Excalidraw canvases.
