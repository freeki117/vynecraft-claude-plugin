---
name: viral
description: "Find what's going viral in a niche or on a topic with VyneCraft: the outlier videos that beat their creator's usual views, with their numbers, hooks and formats, grouped into patterns. Use when the user asks what's working, what's going viral, or for outliers in a niche."
argument-hint: "[niche or topic]"
allowed-tools: mcp__plugin_vynecraft_vynecraft__search_videos mcp__plugin_vynecraft_vynecraft__get_video mcp__vynecraft__search_videos mcp__vynecraft__get_video
---

# /viral: the outliers in a niche

Niche or topic: $ARGUMENTS

1. Call the VyneCraft `search_videos` tool with `niche` set to the niche (or `query` for a topic) and
   `sort: "outlier"`. No niche given: search without one.
2. The defaults are the last 30 days, 25K+ views, 2%+ engagement and 1x+ outlier. Most catalog posts carry no
   posting date, so if fewer than 10 come back, search again with `days: 0` and say you widened it.
3. Read `total_count`. Under about 200: keep calling with `next_cursor` until it is null. More: read the top
   3 pages and say how many of how many you read.
4. Present, numbers first:
   - One line: how many videos matched, the window, what you filtered on.
   - A table of the top 10: creator, views, engagement %, outlier (x their median), format, hook (short), ref.
   - 3-5 patterns across the winners (a format, a hook shape, a topic angle), each with how many videos it rests
     on and their median outlier. Under 5 videos is "too few to trust": say so.
   - What to avoid: anything that shows up among the low outliers.
5. Offer `/teardown` or `/video <ref>` on the best one.

An outlier is views divided by that creator's median views: it says the idea worked, not the audience size. Never
invent a number the tool didn't give. If the VyneCraft tools aren't available, point the user to
https://vynecraft.com/claude to set `VYNECRAFT_API_KEY`.
