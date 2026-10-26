---
name: custom-style
description: Design a new Instagram carousel style for a creator in HandlePilot - layout, palette, type, decoration - plus its first finished deck, held to the same contract as HandlePilot's own designer. Use when no style in list_carousel_styles fits the creator's look and the user wants a carousel format of their own. Custom styles are on HandlePilot's paid plan.
---

# Designing a custom carousel style

Use this when no style in list_carousel_styles fits the creator's look and the user wants one of their own. You design the format - layout, palette, type, decoration, the idea of the thing - and write its first deck. create_custom_style holds it to the same contract and sanitizer as HandlePilot's own designer.

## Before you design

1. **Read the creator:** get_creator_context for the niche, the audience language and the voice.
2. **Read the contract:** call get_playbook with name "custom-style". It returns HandlePilot's design contract: what the manifest must contain (slide kinds, fields, character limits, deck length), the markup rules, the fonts you may use, and three complete example manifests to match. It is the format specification create_custom_style checks against, and it changes with HandlePilot's carousel engine, so read the current version each time rather than working from memory.
3. **Look at the references:** when the user points to reference images, look at them with get_asset (the thumbnail comes back as an image) and pass their ids as referenceAssetIds.

## Through the tools

- Photos: an image field's value is {"assetId": "<an image asset id from this workspace>"} (list_assets, search_assets). Wherever the contract says "handle", read "asset id".
- Send name, brief (the user's own words), template (the manifest) and deck to create_custom_style.
- Problems come back as sentences. Fix them and send the whole thing again. fixedForYou lists harmless repairs the checker made on its own.
- The saved style shows up first in list_carousel_styles and in the app's style picker, and its first deck opens in the Carousel Maker. Give the user the url.
- Later decks in the style: use the carousel skill with the new style id.

## On a free account

create_custom_style is a paid-plan tool and answers upgrade_required on a free account. Tell the user once what it would do and give them the link. Then offer the closest built-in style from list_carousel_styles and build the carousel there with the carousel skill.
