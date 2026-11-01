---
name: remix
description: "Remix a proven catalog post (a slideshow or wall of text) into a post for the user's brand with VyneCraft: the proven words stay, the blanks are written for the brand, every claim is checked. Use when the user wants to turn a proven post into their own."
argument-hint: "<catalog ref> [account]"
allowed-tools: mcp__plugin_vynecraft_vynecraft__get_video mcp__plugin_vynecraft_vynecraft__get_remix mcp__plugin_vynecraft_vynecraft__get_workspace mcp__vynecraft__get_video mcp__vynecraft__get_remix mcp__vynecraft__get_workspace
---

# /remix: a proven post, made yours

Post: $ARGUMENTS

1. No ref given: suggest `/viral` to find one and stop. A `teardown:` ref can't be remixed: remixes start from
   catalog posts (`catalog:…`).
2. Call the VyneCraft `get_video` tool with the ref. If `remix.remixable` is false, say why (`remix.why`) and stop.
3. If an account was named, call `get_workspace` to find its `account_id`. Otherwise the workspace's first account's
   brand is used, as in the studio.
4. Each remix uses one of today's remixes. If the user named this exact post in the command, start it; if you picked
   the post yourself, ask first. Call `start_remix` with `proven_post_id` (and `account_id` if any).
5. Call `get_remix` with the id about every 15 seconds until `status` is `ready`, `blocked` or `failed` (usually 20 to
   60 seconds).
6. Present:
   - **Ready:** every slide's text in order, then the caption, the hashtags and the first comment, ready to copy.
     Then one line on why it should work (`why`) and the studio link (`studio_url`) to make the images.
   - **Blocked:** the claim that blocked it (`blocked_by`), word for word; the user fixes it in the studio.
   - **Failed:** the error, and offer to try another post.
