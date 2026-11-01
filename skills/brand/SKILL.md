---
name: brand
description: "Read the user's brand profile in VyneCraft: content angles, buyer personas with their pains and wants, the voice do's and don'ts, positioning and competitors. Use before writing hooks, scripts or posts for the user's brand, or when they ask what VyneCraft knows about their brand."
argument-hint: "[brand or account name]"
allowed-tools: mcp__plugin_vynecraft_vynecraft__get_brand_profile mcp__plugin_vynecraft_vynecraft__get_workspace mcp__vynecraft__get_brand_profile mcp__vynecraft__get_workspace
---

# /brand: the brand profile

Brand: $ARGUMENTS

1. No brand named: call the VyneCraft `get_brand_profile` tool with nothing (the default brand). A brand or account
   named: call `get_workspace` first, find its `brand_id` or `account_id`, then `get_brand_profile` with it.
2. `status: "none"` means no profile yet: say it's built on the Brand page of the studio (`brand_url`) from the
   brand's website, in about 25 seconds.
3. Present:
   - One line: what the brand sells and to whom (from the brief).
   - **Angles:** the content angles, one line each.
   - **Personas:** each with their top pain and top want.
   - **Voice:** the do's and don'ts, word for word.
   - **Positioning:** the market, the competitors, what sets the brand apart.
   - Anything in `needs_input`: the sections the user should fill in.
4. Offer `/viral-hooks` to write hooks in this voice, or `/remix` to make a post.
