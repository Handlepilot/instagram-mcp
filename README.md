# HandlePilot MCP

<!-- The registry badge works once com.handlepilot/handlepilot is published (RUNBOOK step 7). -->
[![MCP Registry](https://img.shields.io/badge/MCP_Registry-com.handlepilot%2Fhandlepilot-4b5563)](https://registry.modelcontextprotocol.io/v0.1/servers?search=com.handlepilot/handlepilot)
<!-- Add after the Glama connector exists (RUNBOOK step 9):
[![HandlePilot MCP connector](https://glama.ai/mcp/connectors/com.handlepilot/handlepilot/badges/score.svg)](https://glama.ai/mcp/connectors/com.handlepilot/handlepilot)
-->

**An Instagram content hub for your AI agent.** Connect Claude, ChatGPT, Claude Code, Codex, Cursor or VS Code to HandlePilot. Your agent researches, plans and writes on your own AI subscription. HandlePilot keeps your workspaces, competitor research, content plan, board, assets, carousels and reels, watches videos for the agent, and holds the editors where you review every word.

- **Server:** `https://app.handlepilot.com/mcp` (remote, Streamable HTTP)
- **Sign-in:** OAuth in your browser (email sign-in link, then Allow), or a personal token
- **Docs:** https://handlepilot.com/mcp

This repository holds the public docs, the [MCP Registry](https://registry.modelcontextprotocol.io) entry (`server.json`) and a Claude Code plugin with HandlePilot's playbooks as skills. The server itself is run by HandlePilot and is not in this repository.

## What your agent can do

- **Research:** look up any public Instagram account or post, search profiles and reels, rank what performs for your competitors, and watch reels to get a full breakdown: transcript, scenes, hook, structure, music and why it works.
- **Plan:** write a content strategy from your arena and your own numbers, save it as your content plan, and put the ideas on your calendar.
- **Make:** remix proven posts into scripts in your voice, write carousels into HandlePilot's designs (or design a style of your own), and upload reels it cut on your computer.
- **Remember:** your voice guide, plan, board, assets and decks live in HandlePilot, so every agent session starts from the same place.

## Free and paid

Everyone who signs in gets a free account. Nothing runs on your computer and there is no key to copy: the first connection opens a HandlePilot sign-in in your browser.

| | Free | Paid, $50/month, cancel anytime |
|---|---|---|
| Playbooks, prompts, carousel styles and other knowledge tools | Unlimited | Unlimited |
| New video watches (watching a video again is free) | 3 a month | Larger allowance |
| Instagram lookups (accounts, posts, search) | 30 a month | Larger allowance |
| Workspaces (Instagram accounts you manage) | 1 | More |
| Inspiration accounts | Up to 5 per workspace, added by hand | Plus bulk research scans |
| Carousels | 5 a month, in the built-in styles | Included, plus custom styles |
| Production board and calendar | | Included |
| Asset library and uploads | | Included |
| Reels (Reel Maker, finished-reel uploads) | | Included |

- Free allowances reset at the start of each calendar month (UTC).
- Every tool is visible on every account. When a tool needs the paid plan, or a free allowance is used up, it answers `upgrade_required` with a link, and your agent tells you once. Everything you already saved stays usable.
- Upgrade in the app: https://app.handlepilot.com/subscribe. The same connection keeps working; there is nothing to reinstall.

## Install

Every client connects to the same URL: `https://app.handlepilot.com/mcp`.

### Claude (claude.ai, Claude Desktop, mobile)

[![Add to Claude](https://img.shields.io/badge/Claude-Add_HandlePilot-d97757)](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=HandlePilot&connectorUrl=https%3A%2F%2Fapp.handlepilot.com%2Fmcp)

1. Open the link above, or go to **Customize → Connectors**, select **+ Add**, then **Add custom connector**. Name it HandlePilot and paste the URL.
2. Select **Add**, sign in to HandlePilot and press **Allow**.
3. In a chat, turn it on under **+ → Connectors**.

On Team and Enterprise plans an owner adds it once under **Organization settings → Connectors**, and each member then selects **Connect**. On Claude's free plan you can add one custom connector.

<!-- Claude directory listing: add the link here once it is live (RUNBOOK step 11). -->

### ChatGPT

1. Open [chatgpt.com/plugins](https://chatgpt.com/plugins), select **+**, then **Add custom MCP server**.
2. Name it HandlePilot, paste the URL, choose **OAuth** for authentication, accept the warning and select **Create as a plugin**.
3. Sign in to HandlePilot and press **Allow**. In a chat, type **@** and pick HandlePilot.

Your ChatGPT plan and workspace settings decide whether you can add custom MCP servers.

### Claude Code

```bash
claude mcp add --transport http handlepilot https://app.handlepilot.com/mcp
```

Add `--scope user` to use it in every project. Then type `/mcp`, pick **handlepilot**, choose **Authenticate**, sign in and press **Allow**.

**Or install the plugin**, which adds the same server plus HandlePilot's playbooks as skills (`/handlepilot:strategy`, `/handlepilot:remix`, ...):

```text
/plugin install handlepilot --marketplace Handlepilot/instagram-mcp
```

On Claude Code older than 2.1.275, run `/plugin marketplace add Handlepilot/instagram-mcp`, then `/plugin install handlepilot@handlepilot`. Then type `/mcp`, pick **plugin:handlepilot:handlepilot**, choose **Authenticate**, sign in and press **Allow**.

Use one or the other. With both, Claude Code connects twice and lists every tool twice; remove the manual one with `claude mcp remove handlepilot`.

### Codex

```bash
codex mcp add handlepilot --url https://app.handlepilot.com/mcp
codex mcp login handlepilot
```

Or in `~/.codex/config.toml`:

```toml
[mcp_servers.handlepilot]
url = "https://app.handlepilot.com/mcp"
```

then run `codex mcp login handlepilot`.

### Cursor

[![Install in Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en/install-mcp?name=handlepilot&config=eyJ1cmwiOiJodHRwczovL2FwcC5oYW5kbGVwaWxvdC5jb20vbWNwIn0%3D)

Or add it to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "handlepilot": {
      "url": "https://app.handlepilot.com/mcp"
    }
  }
}
```

Cursor asks you to sign in to HandlePilot the first time it connects.

### VS Code

[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_HandlePilot-0098FF)](https://vscode.dev/redirect/mcp/install?name=handlepilot&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapp.handlepilot.com%2Fmcp%22%7D)

Or from a terminal:

```bash
code --add-mcp '{"name":"handlepilot","type":"http","url":"https://app.handlepilot.com/mcp"}'
```

Or in `.vscode/mcp.json`:

```json
{
  "servers": {
    "handlepilot": {
      "type": "http",
      "url": "https://app.handlepilot.com/mcp"
    }
  }
}
```

VS Code opens the HandlePilot sign-in in your browser on first use.

### Other clients

Any MCP client that supports remote Streamable HTTP servers with OAuth can use `https://app.handlepilot.com/mcp`.

### A personal token instead of OAuth

For clients that can't do OAuth, or for scripts:

1. Sign in at https://app.handlepilot.com/connect-ai and create a token. It starts with `hp_` and is shown once.
2. Send it as a header: `Authorization: Bearer hp_YOUR_TOKEN`.

```bash
# Claude Code
claude mcp add --transport http handlepilot https://app.handlepilot.com/mcp \
  --header "Authorization: Bearer hp_YOUR_TOKEN"
```

```toml
# Codex: put the token in an environment variable, e.g. export HANDLEPILOT_TOKEN="hp_YOUR_TOKEN"
[mcp_servers.handlepilot]
url = "https://app.handlepilot.com/mcp"
bearer_token_env_var = "HANDLEPILOT_TOKEN"
```

```json
// Cursor: ~/.cursor/mcp.json
{
  "mcpServers": {
    "handlepilot": {
      "url": "https://app.handlepilot.com/mcp",
      "headers": { "Authorization": "Bearer hp_YOUR_TOKEN" }
    }
  }
}
```

A token reaches every workspace you manage, with the same rights as you in the app. Revoke it on the same page at any time; it stops working at once.

## Tools

39 tools. Every account sees all of them; the plan decides which ones run.

**Free**

| Tool | What it does |
|---|---|
| `list_workspaces` | The Instagram accounts you manage in HandlePilot |
| `get_creator_context` | Profile, niche, audience language, voice guide and samples, plan and board summary. Read first |
| `update_voice_pack` | Save how the creator talks and writes |
| `get_my_performance` | The creator's own 30-day Instagram numbers (needs the Instagram connection made in the app) |
| `list_inspiration_accounts` | The competitor and inspiration watch-list, best first |
| `verify_inspiration_accounts` | Mark accounts on the list as verified, on your word |
| `remove_inspiration_account` | Take an account off the list |
| `list_top_content` | The best recent posts across the watch-list, with cached video breakdowns inline |
| `get_content_plan`, `save_content_plan` | Read or save the content strategy |
| `list_carousel_styles`, `get_carousel_style` | HandlePilot's carousel designs and the writing brief for each |
| `list_carousels`, `get_carousel`, `update_carousel` | Your carousels; revise a deck |
| `get_playbook` | HandlePilot's how-to guides (the same texts as the plugin's skills) |
| `send_feedback` | Tell the HandlePilot team what to fix, add or change |

**Free, within the monthly allowances**

| Tool | What it does | Free allowance |
|---|---|---|
| `watch_video` | A structured breakdown of a reel, a post or an asset: transcript, on-screen text, scenes, hook, structure, music, editing, why it works | 3 new videos a month; watching again is free |
| `get_instagram_account` | A public profile and its recent posts with numbers | 30 lookups a month, shared by these three tools |
| `get_instagram_post` | One post: caption, numbers, author, media links | |
| `search_instagram` | Search Instagram profiles, or this month's reels on a topic | |
| `create_workspace` | Add an Instagram account as a workspace | 1 workspace |
| `add_inspiration_accounts` | Add accounts to the watch-list for you to verify | Up to 5 per workspace |
| `create_carousel` | Write a carousel into a style, editable in the Carousel Maker | 5 a month, built-in styles |

**Paid plan**

| Tool | What it does |
|---|---|
| `scan_instagram_accounts` | Bulk research: screen up to 20 accounts in one call |
| `list_cards`, `get_card`, `create_card`, `update_card`, `delete_card` | The production board and calendar, scripts included |
| `create_custom_style` | Design a carousel style of your own, plus its first deck |
| `list_assets`, `search_assets`, `get_asset`, `import_asset_from_url`, `create_upload_link` | The asset library, searchable by meaning; an upload page for files too big for the chat |
| `start_asset_upload` | Upload a file from your computer into the asset library * |
| `list_reels`, `start_reel_upload` | The Reel Maker, and finished reels your agent cut * |

\* `start_asset_upload` and `start_reel_upload` are offered only to agents that run on your computer, such as Claude Code. Chat apps such as ChatGPT and claude.ai don't get them.

The server also serves its playbooks as MCP prompts: `getting-started`, `strategy`, `discovery`, `voice-pack`, `remix`, `carousel`, `custom-style`, `reel-editing`.

## Example prompts

- "Look up @yourhandle on HandlePilot and tell me which of my last 30 posts beat my usual views, and why."
- "Watch this reel and break down the hook, the structure and why it works: https://www.instagram.com/reel/..."
- "Build my voice guide from my recent posts and save it to HandlePilot."
- "Write a 7-slide carousel about meal prep for busy parents in one of HandlePilot's styles, in my voice."
- "Study my competitors and write me a content strategy for the next month."
- Paid plan: "Find 25 accounts in my niche I should learn from and add them to my inspiration list."
- Paid plan: "Turn the strongest idea from my plan into a ready-to-shoot script on my board for next Tuesday."

## The Claude Code plugin

`plugins/handlepilot/` is a Claude Code plugin, listed in this repository's marketplace (`.claude-plugin/marketplace.json`). It declares the remote server in `.mcp.json` and turns HandlePilot's playbooks into eight skills: getting-started, strategy, discovery, voice-pack, remix, carousel, custom-style and reel-editing. It runs no local code. See [plugins/handlepilot/README.md](plugins/handlepilot/README.md).

## Your data

- A connected app or token reaches every workspace you manage, with the same rights as you in the app. Disconnect an app or revoke a token on https://app.handlepilot.com/connect-ai at any time.
- What a tool returns is read by your agent's AI provider (for example OpenAI for ChatGPT and Codex, Anthropic for Claude), under your agreement with them.
- Public Instagram data is fetched on demand by HandlePilot. Nothing is posted to Instagram through your agent.
- Privacy policy: https://handlepilot.com/privacy
- Terms: https://handlepilot.com/terms

## Support

- Email: support@handlepilot.com
- Bugs and requests: [open an issue](https://github.com/Handlepilot/instagram-mcp/issues/new/choose). Never paste a token (`hp_...`) into an issue.
- From your agent: ask it to send feedback; HandlePilot's `send_feedback` tool reaches the team directly.

## License

The files in this repository (docs, `server.json`, the plugin and its skills) are MIT licensed; see [LICENSE](LICENSE). The HandlePilot service is covered by its [terms](https://handlepilot.com/terms).

HandlePilot is an independent product. It is not affiliated with, endorsed by or sponsored by Instagram or Meta. Instagram is a trademark of Meta Platforms, Inc.
