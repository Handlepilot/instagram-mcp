# Changelog

Changes to this repository: the docs, `server.json` and the Claude Code plugin. The HandlePilot server is deployed separately; its tools can change without a release here.

Versions follow the plugin's `version` in `plugins/handlepilot/.claude-plugin/plugin.json`. A registry metadata change gets a new `version` in `server.json` (registry versions can't be reused).

## 1.0.0 (2026-10-26)

- First public release.
- README: what HandlePilot does, free and paid plans, install for Claude, ChatGPT, Claude Code, Codex, Cursor and VS Code, the personal-token option, the 39 tools by plan, example prompts.
- `server.json` for the official MCP Registry: `com.handlepilot/handlepilot`, remote Streamable HTTP at `https://app.handlepilot.com/mcp`.
- Claude Code plugin `handlepilot` and marketplace `handlepilot`: the remote server plus eight skills (getting-started, strategy, discovery, voice-pack, remix, carousel, custom-style, reel-editing).
