---
name: teardown
description: "Tear down any TikTok or YouTube video link with VyneCraft, Shorts and long videos too: its real numbers, the hook word for word, why it worked, the structure, format and call to action. Use when the user pastes a video link and asks to tear it down, analyze it, or explain why it went viral. Takes one link or several."
argument-hint: "<video link> [more links]"
allowed-tools: mcp__plugin_vynecraft_vynecraft__teardown_video mcp__plugin_vynecraft_vynecraft__get_video mcp__plugin_vynecraft_vynecraft__get_transcript mcp__vynecraft__teardown_video mcp__vynecraft__get_video mcp__vynecraft__get_transcript
---

# /teardown: why did this video work?

Links: $ARGUMENTS

1. For each link, call the VyneCraft `teardown_video` tool with `url` set to the link. Several links: one call per
   link, then report them together. No link given: ask for one and stop.
   - For an Instagram Reel link that doesn't name the creator, ask for the creator's @handle and pass it as
     `instagram_handle` (only if the tool's description lists Instagram).
   - If the tool answers with an error, show its sentence as it is (bad link, unsupported platform, a private or
     removed video, or today's limit) and stop for that link. Don't retry a limit.
   - `already_had: true` means the workspace tore this one down before: say so, it cost nothing.
2. The answer has the numbers, caption, hook and transcript size at once. The deep analysis lands about a minute
   later: while `teardown.deep_analysis.state` is `analyzing`, wait about 30 seconds and call `get_video` with the
   `ref`, up to 4 times. If the state is `queued`, `cap` or `no-words`, report what's there and quote the state's
   `title` (the analysis shows up later in the studio).
3. Present each video like this, short and specific, numbers first:

   **@creator · Platform · 1.2M views · 4.1% engagement · 3.2x their median**
   - **Hook:** the spoken hook word for word (`deep_analysis.hook.spoken`), its type (`hook.type.name`) and the
     formula with [blanks] (`hook.formula`).
   - **Why it worked:** 2-3 sentences from `hook.why_it_works`, `summary` and `angle`. No filler.
   - **Structure:** `storytelling_structure.name`, then the sections in order with their start times.
   - **Format and layout:** `format.name`, `visual_layout.name`. **Call to action:** `call_to_action`.
   - **Steal this:** one or two lines on how the user could use the same structure for their own topic (copy the
     structure, never the video).
   - The `studio_url` link.

   Use the 90-day score (`deep_analysis.outlier_90d`) when it has one, else `outlier.x`. Leave out any number the
   tool doesn't give; never estimate one. Several videos: a table first (creator, views, engagement, outlier, hook
   type, structure), then the patterns they share, then one line each.
4. Want every word? `get_transcript` with the `ref`.

If the VyneCraft tools aren't available, tell the user to set `VYNECRAFT_API_KEY` to a key from VyneCraft's
Settings → API keys and restart Claude Code (the setup page: https://vynecraft.com/claude).
