---
name: voice-pack
description: Learn how an Instagram creator talks and writes from their own posts, and save a voice guide in HandlePilot that every script and caption follows. Use when the user asks for a tone of voice, brand voice or writing style guide, or when get_creator_context shows no voice guide before you write scripts or captions for that creator.
---

# Building the creator's voice pack

Goal: a voice guide that makes every script and caption sound like this creator, saved with update_voice_pack. HandlePilot's own remix, carousel and plan generators read it too.

1. **Read what HandlePilot has.** get_creator_context: read voice.samples (recent reel transcripts and captions, when HandlePilot has built them) and any existing guide.
2. **Gather more when the samples are thin.** get_instagram_account on their handle (posts: 15-24) for captions. For speech, watch_video on 5-8 of their reels (cached once watched), or, with a computer, get_instagram_post for the video links, download them and transcribe locally (for example with whisper) to save watches.
3. **Study, concretely:**
   - Spoken: sentence length, pace, energy; how they open (question, claim, story); signature phrases and fillers they keep; humour; how they address the viewer; any language mixing.
   - Written: caption structure (hook line, line breaks, lists), length, emoji (which, where, how many), hashtags (count, placement), the calls to action they use, capitalisation and punctuation quirks.
   - Topics and stances they return to; words and claims they never use.
4. **Write the guide** in markdown, 300-1200 words, under these headings: How they talk / How they write captions / Signature moves / Vocabulary (use, avoid) / Do, Don't / Examples (3-6 short verbatim quotes). Make it specific enough that two writers following it would sound alike.
5. **Check it with the user.** Show the guide and ask what is off. Then call update_voice_pack with the guide, and with samples (the transcripts and captions you gathered) when you produced them yourself.

## On a free account

Account and post lookups count against the 30 Instagram lookups a month, and new watches against the 3 new watches. Lean on the samples HandlePilot already has, captions from one get_instagram_account call, and at most 3 watches. With a computer, local transcription saves the watches. update_voice_pack itself has no limit.
