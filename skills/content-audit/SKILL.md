---
name: content-audit
description: "Audit the user's VyneCraft workspace for a window: how its videos did (hit rates at 1.5x and 4x, the top outliers), the formats that win in the catalog, the latest remixes, and what to make next. Use when the user asks how their content is doing, for a recap, or what to post next."
argument-hint: "[days, default 30]"
allowed-tools: mcp__plugin_vynecraft_vynecraft__get_workspace_recap mcp__plugin_vynecraft_vynecraft__search_videos mcp__vynecraft__get_workspace_recap mcp__vynecraft__search_videos
---

# /content-audit: how it's going and what to make next

Window: $ARGUMENTS

1. Call the VyneCraft `get_workspace_recap` tool with `days` set to the number given (default 30; 0 = all time).
2. If the window has under 5 videos, say so and run it again with `days: 0`.
3. Present, numbers first:
   - **The window:** videos in it, hit rate at 1.5x and at 4x, and n.
   - **What worked:** the top outliers (creator, views, outlier, hook), and what they share.
   - **What drained views:** the low ones and their common thread, if the data shows one (call `search_videos`
     with `kinds: ["teardown", "baseline"]`, `sort: "outlier"` and the same `days` to see them).
   - **The formats that win in the catalog:** share, median views, one example each.
   - **The latest remixes** and their status.
   - **Next batch of 7:** two narrow ideas, one broad one, one wildcard and three more, each tied to a ref above.
4. Keep it short. Under 5 videos in a group is "too few to trust": say so rather than draw a pattern.
