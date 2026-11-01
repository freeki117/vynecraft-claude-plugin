---
name: transcript
description: "Get the full spoken transcript of a video in VyneCraft by its ref, or a catalog post's on-screen words. Use when the user wants every word of a video they tore down or found with VyneCraft."
argument-hint: "<ref, e.g. teardown:…>"
allowed-tools: mcp__plugin_vynecraft_vynecraft__get_transcript mcp__vynecraft__get_transcript
---

# /transcript: every word

Ref: $ARGUMENTS

1. Call the VyneCraft `get_transcript` tool with `ref` set to the ref. No ref given: ask for one (a `/teardown`
   answer has it).
2. When `next_offset` is not null, call again with `offset` set to it until it is null, and join the pieces.
3. Present:
   - One line first: how many words, and the spoken hook (`spoken_hook`).
   - The transcript, cleaned only of the time markers like `[2.1s]`, in short paragraphs. Keep every word.
   - If `available` is false, say why (`why`) and show the caption or the on-screen words instead.
4. Offer to mark where the hook, the setup, the payoff and the call to action are.
