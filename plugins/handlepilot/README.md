# HandlePilot plugin

HandlePilot is an Instagram content hub for your AI agent. Your agent researches, plans and writes; HandlePilot keeps your workspaces, competitor research, content plan, board, assets, carousels and reels, watches videos for the agent, and holds the editors where you review its work.

This plugin connects Claude to the HandlePilot MCP server and adds HandlePilot's playbooks as skills, so Claude knows the order of work and the rules without being told.

## What it contains

- **One remote MCP server**, `handlepilot`, at https://app.handlepilot.com/mcp (Streamable HTTP). The plugin runs no local code: no hooks, no scripts, no local server.
- **Eight skills**, plain instructions that use the server's tools:

| Skill | Use it to |
|---|---|
| getting-started | Learn the main flow, the rules and what the free and paid plans allow |
| strategy | Research the arena and the creator's numbers, then save a content plan with ideas on the calendar |
| discovery | Build a watch-list of 20-30 competitor and inspiration accounts |
| voice-pack | Learn how the creator talks and writes, and save a voice guide |
| remix | Turn a post that performs into a ready-to-shoot script in the creator's voice |
| carousel | Write a carousel into one of HandlePilot's designs, editable word by word |
| custom-style | Design a carousel style of the creator's own, plus its first deck |
| reel-editing | Cut, caption and check a reel with ffmpeg on your computer, then upload it |

In Claude Code the skills run as `/handlepilot:strategy`, `/handlepilot:remix` and so on, and Claude also loads them on its own when a task matches.

## Install in Claude Code

```text
/plugin install handlepilot --marketplace Handlepilot/instagram-mcp
```

That works in one step on Claude Code 2.1.275 or later. On older versions, add the marketplace first:

```text
/plugin marketplace add Handlepilot/instagram-mcp
/plugin install handlepilot@handlepilot
```

Then type `/mcp`, pick plugin:handlepilot:handlepilot, choose Authenticate, sign in to HandlePilot and press Allow.

If you already added the server by hand (`claude mcp add ... handlepilot ...`), remove it with `claude mcp remove handlepilot`, or Claude Code lists every tool twice.

## Sign-in and plans

The first time Claude connects to the server, HandlePilot opens a sign-in page in your browser. You enter your email, open the sign-in link HandlePilot sends, and press Allow. That creates a free account if you don't have one. There is no API key to copy.

- **Free:** the knowledge tools without limit; each month 3 new video watches (repeating a watched video is free), 30 Instagram lookups and 5 carousels in the built-in styles; 1 workspace and up to 5 inspiration accounts added by hand.
- **Pro ($50/month) and Studio ($200/month), plus tax, cancel anytime:** bulk research scans, the production board and calendar, custom carousel styles, the asset library and reels. Pro: 20 workspaces, 500 new video watches and 20,000 tool calls a month. Studio: 120 workspaces, 3,000 watches and 120,000 tool calls. Details: https://handlepilot.com/mcp#plans

Every tool is visible on every account. A paid-only tool answers `upgrade_required` with a link, and the same connection works as soon as you upgrade.

## What it sends and stores

- Tool calls go to HandlePilot over HTTPS, signed in as you. They carry what the agent asks for: handles, post links, scripts, carousel text, plan content and similar.
- HandlePilot stores what you save (workspaces, voice guide, plan, cards, carousels, assets) in your account and logs each tool call with a summary of its arguments.
- Public Instagram data is fetched on demand by HandlePilot. Nothing is posted to Instagram through your agent.
- What a tool returns is read by your AI provider under your agreement with them.
- You can disconnect at any time on the Connect AI page: https://app.handlepilot.com/connect-ai

Privacy policy: https://handlepilot.com/privacy. Terms: https://handlepilot.com/terms.

## Support

Email support@handlepilot.com, or open an issue in this repository. Setup for other clients (ChatGPT, Codex, Cursor, VS Code) is in the repository README and on https://handlepilot.com/mcp.

## License

The plugin's files are MIT licensed (see LICENSE). The HandlePilot service is covered by its terms.

HandlePilot is an independent product. It is not affiliated with, endorsed by or sponsored by Instagram or Meta. Instagram is a trademark of Meta Platforms, Inc.
