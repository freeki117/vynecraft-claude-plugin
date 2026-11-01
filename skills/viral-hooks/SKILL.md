---
name: viral-hooks
description: "Pull the opening hooks that worked, word for word, from VyneCraft's proven videos in a niche, grouped into reusable templates with their numbers, or the hooks the user saved. Use when the user asks for hooks, openers, or how the best videos in a niche start."
argument-hint: "[niche or topic] [saved]"
allowed-tools: mcp__plugin_vynecraft_vynecraft__list_hooks mcp__plugin_vynecraft_vynecraft__get_brand_profile mcp__vynecraft__list_hooks mcp__vynecraft__get_brand_profile
---

# /viral-hooks: the hooks that worked

Niche or topic: $ARGUMENTS

1. Call the VyneCraft `list_hooks` tool with `niche` (or `query`) and `sort: "outlier"`. If the user said "saved",
   pass `source: "saved"` instead: those are the hooks they kept.
2. Fewer than 10 hooks: call again with `days: 0` (most catalog posts have no posting date) and say you widened it.
   Page with `next_cursor` until you have 50 or it is null.
3. Present:
   - 3-5 hook templates with [blanks], e.g. "Stop [doing X]. Do [Y] instead.", each with how many hooks it rests
     on, their median outlier, and 2 real examples word for word with their views.
   - Then the top 10 hooks as a list: the hook word for word, views, outlier, creator.
4. If the user wants hooks for their own brand: call `get_brand_profile`, then write 5 hooks from the top templates
   in the brand's voice, one sentence each, 15 words or fewer, the payoff last, and name the template each came from.

Quote hooks exactly as the tool gives them. Never invent numbers.
