---
name: remixes
description: "List the user's remixes in VyneCraft, newest first, with their status, hook and caption, or open one in full. Use when the user asks about their remixes, drafts, or what's ready to post."
argument-hint: "[ready | blocked | failed | generating] [remix id]"
allowed-tools: mcp__plugin_vynecraft_vynecraft__list_remixes mcp__plugin_vynecraft_vynecraft__get_remix mcp__vynecraft__list_remixes mcp__vynecraft__get_remix
---

# /remixes: what's made, what's ready

Filter: $ARGUMENTS

1. A remix id given: call the VyneCraft `get_remix` tool with it and show it in full (slides in order, caption,
   hashtags, first comment, what blocked it if anything, the studio link). Stop there.
2. Otherwise call `list_remixes`, with `status` if the user named one, `limit: 25`.
3. Present:
   - One line: the total and how many are ready, blocked, generating and failed.
   - A table, newest first: status, hook, where it came from (creator and views of the original), date, studio
     link.
   - Blocked ones first if there are any: they need the user's fix in the studio.
4. Offer to open one in full (`/remixes <id>`) or start a new one (`/remix`).
