---
name: workspace
description: "Show the user's VyneCraft workspace: its accounts, brand profiles, how much data it holds, and today's limits (teardowns, remixes, API calls). Use first when connecting VyneCraft, or when the user asks what's in their workspace or how many teardowns or remixes they have left today."
allowed-tools: mcp__plugin_vynecraft_vynecraft__get_workspace mcp__vynecraft__get_workspace
---

# /workspace: what this key reads

1. Call the VyneCraft `get_workspace` tool.
2. Present, short:
   - **Workspace:** the name.
   - **Accounts:** each handle and platform, and which brand it uses.
   - **Brands:** each with its status; say which is the default. No ready brand: say it's built on the studio's
     Brand page before any remix.
   - **Data:** catalog posts, teardowns, baseline rows, remixes.
   - **Today:** teardowns used and left, remixes used and left (or "no daily cap"), and the key's limits (calls a
     minute and a day, teardowns a day).
3. Then list the 10 VyneCraft skills in one line each: /teardown, /viral, /video, /transcript, /viral-hooks,
   /content-audit, /brand, /remix, /remixes, /workspace.

If the tool isn't available or answers that the key is missing or invalid: the user sets `VYNECRAFT_API_KEY` to a
key from VyneCraft's Settings → API keys and restarts Claude Code (https://vynecraft.com/claude).
