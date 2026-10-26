---
name: reel-editing
description: Cut and caption an Instagram reel on the user's computer with ffmpeg - pull footage from HandlePilot, keep captions inside Instagram's safe zone, check the cut, and upload the finished reel to HandlePilot. Use in an agent with a shell (Claude Code, Codex, Cursor) when the user wants a reel edited from footage or from a script card, including split-screen reels.
---

# Editing reels on your computer

For agents with a shell (Claude Code, Codex, Cursor). HandlePilot stores the footage and posts the result; you cut with ffmpeg on the user's machine. Ask before installing anything (ffmpeg, whisper).

1. **Plan:** a card with a script (the remix skill) or the user's brief. Note each scene and its A/B roll.
2. **Footage:** search_assets for each B-roll scene ("hands chopping onions"); get_asset gives a one-hour download link: curl -L -o clip.mp4 '<url>'. For the user's own A-roll, ask for the file path.
3. **Inspect:** ffprobe -v error -show_entries format=duration:stream=width,height,r_frame_rate -of json clip.mp4
4. **Cut and assemble** at 1080x1920, 30 fps:
   - Trim and normalise: ffmpeg -ss 2.0 -to 5.5 -i in.mp4 -vf "scale=1080:1920:force_original_aspect_ratio=increase,crop=1080:1920,fps=30" -c:v libx264 -crf 20 -preset medium -c:a aac -b:a 160k part1.mp4
   - Join: list the parts in parts.txt (file 'part1.mp4', one per line), then ffmpeg -f concat -safe 0 -i parts.txt -c copy joined.mp4
   - Voiceover or music: add -i voice.m4a -map 0:v -map 1:a -shortest; keep music well under speech (sidechaincompress, or about -18 LUFS).
5. **Captions:** transcribe the voice with word timings (whisper or whisper.cpp with word timestamps), write an .ass file, and burn it in with -vf "ass=captions.ass".
   Instagram's safe zone on 1080x1920, the numbers HandlePilot's own renderer uses: keep text at least 270 px from the top, 500 px from the bottom and 65 px from each side; the username row, caption and buttons cover the rest. 2-4 words per caption page, high contrast, 64-90 px type.
6. **Check:** upload the cut as an asset (start_asset_upload), then watch_video on it with a question such as "List every problem: cut timing, captions colliding with the safe zone, audio level, pacing, the first second." Fix and repeat.
7. **Deliver:** H.264 + AAC MP4, 9:16, under 100 MB (re-encode with -crf 23 if bigger). start_reel_upload, then curl -T reel.mp4 to the upload url. Move the card on with update_card (post_production or ready_to_publish). The user posts it from the Reel Maker, as a reel or a trial reel.

## Split screen (a talking head on top, an explainer panel below), a first version

1. Transcribe the take with word timings and split it into beats (one idea each).
2. Frame the head: crop the speaker into the top 1080x960, face centred.
3. Author the panel, the bottom 1080x960: for every beat, a visual that shows what is being said - a few words of text, a screenshot, a diagram, an asset.
4. Render the panel frames with what you have (HTML and a headless browser, ImageMagick, or stills from assets) and time them to the beats.
5. Composite: ffmpeg -i top.mp4 -i panel.mp4 -filter_complex "[0:v][1:v]vstack=inputs=2" -c:a copy out.mp4, then captions as above, inside the safe zone.

## On a free account

The asset library and reels are on the paid plan: search_assets, get_asset, start_asset_upload, list_reels and start_reel_upload answer upgrade_required. Tell the user once and give them the link. You can still cut a reel from files the user points you to on their computer: follow steps 3-5, skip the upload check, and hand back the finished MP4's path for them to post.
