---
name: video
description: "Open one video from VyneCraft in full by its ref (from /viral, /teardown or /viral-hooks): numbers, outlier, hook, format, the deep analysis and top comments. Use when the user asks about one specific video in their VyneCraft results."
argument-hint: "<ref, e.g. teardown:… or catalog:…>"
allowed-tools: mcp__plugin_vynecraft_vynecraft__get_video mcp__vynecraft__get_video
---

# /video: one video in full

Ref: $ARGUMENTS

1. Call the VyneCraft `get_video` tool with `ref` set to the ref. No ref given: ask for one, or suggest `/viral` to
   find videos. A video link instead of a ref: use `/teardown` on it instead.
2. Not found: say the ref isn't in this workspace or the catalog.
3. Present, numbers first:
   - **@creator · Platform · views · engagement % · outlier (x their median)** and the posting date.
   - The hook word for word, and on a teardown its type and formula from `deep_analysis.hook`.
   - Why it worked (`deep_analysis.summary`, `hook.why_it_works`), the structure and the sections in order, the
     format, the layout and the call to action. If `deep_analysis.state` isn't `ready`, quote its `title` instead.
   - A catalog post: its slides or on-screen words, and whether it can be remixed (`remix.remixable`).
   - The top 3 comments by likes, if there are any, and what they react to.
   - The link (`url`) and the studio link (`studio_url`).
4. Offer the next step: `/transcript <ref>` for every word, or `/remix <ref>` when the post can be remixed.

Never fill in a number the tool didn't return.
