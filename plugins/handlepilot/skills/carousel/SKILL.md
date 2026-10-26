---
name: carousel
description: Write an Instagram carousel into one of HandlePilot's designs so every word stays editable in the Carousel Maker. Use when the user asks for a carousel, slides, a swipe post or a slide deck for Instagram. Do not render slides as images or HTML yourself; write into a HandlePilot style instead.
---

# Building an editable carousel

Goal: a finished carousel in one of HandlePilot's designs, every word editable in the Carousel Maker.

The rule: never render images or HTML of your own, and never paste slide text into a card instead. Write into a style's slots with create_carousel, so the user can edit, re-theme and export it.

1. **Read the creator:** get_creator_context for the voice and the audience language.
2. **Pick a style:** list_carousel_styles. Pick by fit: the topic and register (bestFor, vibe); photo-led styles (needsPhotos) only when photosInLibrary can fill them; cyrillic: true when the audience writes Cyrillic. The workspace's own styles (own: true) come first; prefer them when they fit.
3. **Read the brief:** get_carousel_style. Read the whole brief: slide kinds, every field's guide and character cap, rows, the deck length, and the photos list.
4. **Photos,** for styles with image slots: per slide, search_assets or the style's photos list, following each slot's own instruction (crop, empty space, "same as the cover"). Use asset ids. No good photo? Ask the user for one, or, with a computer, upload it yourself with start_asset_upload.
5. **Write the deck:** the first kind first, the last kind last, body slides between them within the stated count. Fill every required field and aim at each field's suggested length; the caps are characters and they are hard. Slide 1 is a promise, slide 2 re-hooks, one idea per slide, proof near the end, then a call to action (save, send, or a comment keyword).
6. **Save it:** create_carousel. If it answers problems, fix exactly those and send the whole deck again; usually one round is enough.
7. **Hand it over:** give the user the editor url. To tie it to the board, add the url to a card's note (create_card or update_card).

To revise: get_carousel, change the slides, then update_carousel with the whole deck (the style stays).

## On a free account

- A free account makes 5 carousels a month, in the built-in styles. The answer's freePlan field says how many are left.
- The asset library is on the paid plan, so choose a style that doesn't need photos (needsPhotos: false) unless the user is on the paid plan.
- Workspace styles (own: true) and the board are paid features too. If a call answers upgrade_required, give the user its link once and keep going with a built-in style.
