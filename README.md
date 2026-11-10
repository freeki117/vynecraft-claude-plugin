# VyneCraft for Claude Code

The VyneCraft plugin puts your VyneCraft workspace inside Claude Code: tear down any TikTok or YouTube video, find the
outliers in your niche, pull the hooks that worked, and turn a proven post into one for your brand. It gives Claude
10 skills and connects VyneCraft's MCP server (`https://app.vynecraft.com/api/mcp`) with your own API key.

Setup guide with screenshots: https://vynecraft.com/claude

## The 10 skills

| Type | What it does |
|---|---|
| `/teardown <link>` | Tears down a TikTok or YouTube video (Shorts and long videos): the numbers, the hook, why it worked, the structure. Paste several links to compare them. |
| `/viral [niche]` | The outlier videos in a niche: the ones that beat their creator's usual views, grouped into patterns. |
| `/video <ref>` | One video in full: numbers, outlier, hook, the deep analysis, top comments. |
| `/transcript <ref>` | Every spoken word of a video you tore down. |
| `/viral-hooks [niche]` | The opening hooks that worked in a niche, grouped into patterns with their numbers. |
| `/content-audit [days]` | How your workspace's videos did, what won, what drained views, and 7 ideas for next. |
| `/brand` | Your brand profile: angles, personas, voice do's and don'ts. |
| `/remix <ref>` | Turns a proven slideshow or wall of text into a post for your brand. |
| `/remixes` | Your remixes, newest first, and what's ready to post. |
| `/workspace` | Your workspace, its brands, and today's limits. |

If another skill or command already uses one of these names, type it with the plugin's name in front, like
`/vynecraft:teardown`.

## Install

You need Claude Code and a VyneCraft account (VyneCraft is in early access: https://vynecraft.com).

1. **Get an API key.** Sign in at https://app.vynecraft.com, open **Settings → API keys** and press
   **Issue new key**. Copy it right away: it's shown once.
2. **Put the key in an environment variable** called `VYNECRAFT_API_KEY`, in the shell you start Claude Code from.
   Never paste the key into a file you share or commit.
   - macOS or Linux: add `export VYNECRAFT_API_KEY="vyne_sk_..."` to `~/.zshrc` or `~/.bashrc`, then open a new
     terminal.
   - Windows (PowerShell): `setx VYNECRAFT_API_KEY "vyne_sk_..."`, then open a new terminal.
3. **Install the plugin.** From this folder (a copy of the repository on your machine):
   ```
   claude plugin marketplace add ./integrations/claude-plugin
   claude plugin install vynecraft@vynecraft
   ```
   Or load it for one session without installing: `claude --plugin-dir ./integrations/claude-plugin`.
4. **Check it.** Start Claude Code, run `/mcp`: `plugin:vynecraft:vynecraft` should say connected. Then type
   `/teardown` and paste a TikTok or YouTube link.

Already added the server by hand with `claude mcp add ... vynecraft`? Remove that one (`claude mcp remove vynecraft`)
so Claude doesn't see every tool twice.

## Without the plugin

The MCP server works on its own too. One line, in any project:

```
claude mcp add --transport http vynecraft https://app.vynecraft.com/api/mcp --header "Authorization: Bearer <your key>"
```

That gives Claude the tools but not the 10 skills.

## Limits

Every teardown and remix counts against your workspace's daily limits, the same as in the studio. On top of that,
each API key gets 2,000 calls a day, 60 a minute, and 30 teardowns a day. Revoke a key any time in Settings → API
keys.

## claude.ai and Claude Desktop

The claude.ai and Claude Desktop connectors sign in with OAuth, which VyneCraft doesn't support yet: coming soon.
Today the plugin and the server work in Claude Code.

## Files

`.claude-plugin/plugin.json` (the manifest), `.claude-plugin/marketplace.json` (this folder is also a one-plugin
marketplace), `.mcp.json` (the server, with the key read from `VYNECRAFT_API_KEY`), `skills/<name>/SKILL.md` (the 10
skills). Check it with `claude plugin validate ./integrations/claude-plugin`.
