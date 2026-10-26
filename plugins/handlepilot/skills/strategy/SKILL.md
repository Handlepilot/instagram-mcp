---
name: strategy
description: Write an Instagram content strategy with HandlePilot - research the creator's arena and their own numbers, ask where they want to go, and save a content plan whose ideas land on the calendar. Use when the user asks for a content strategy, content plan, content pillars, posting cadence or content calendar for an Instagram account, or when get_creator_context shows no plan.
---

# Writing a content strategy

Goal: a plan this creator will actually follow, saved with save_content_plan, its ideas landed on the calendar.

1. **Read the creator.** get_creator_context: profile, niche brief, voice, any existing plan, the board. If a plan exists, ask the user whether to revise it or start fresh.
2. **Read their own numbers.** get_instagram_account on their own handle (posts: 24-36): which posts beat their median, which formats and topics. When instagramConnected is true, get_my_performance adds reach, follower growth and their top posts.
3. **Read the arena.** list_inspiration_accounts. If it is thin (fewer than about 15 accounts that fit), build it first with the discovery skill. Then list_top_content (reels, then posts).
4. **Watch the winners.** watch_video on the 5-10 best performers that fit this creator. Check "watched" first: cached watches are free. Note the formats, hooks and structures that repeat.
5. **Ask the creator,** in one message of 3-5 questions: where should the account be in three months (followers, leads, a launch)? What can they realistically make each week (time, on camera or not, setup)? Anything off-limits?
6. **Write the plan:**
   - positioning: one sentence - one person, one problem, a point of view. A stranger reading three posts could say it back.
   - pillars: 3-5, each with a job - attract (built for strangers), nurture (trust, personality), convert (activates buyers). Aim for about 70/20/10 across the ideas.
   - mix: reels / carousels / photos, grounded in what performs in this arena and for this creator. Strong accounts in a space measured about 63/32/5; with no data, start nearer 40/30/20.
   - cadence: posts per week they can sustain. 3 is the floor, about 5 is strong; sustainable beats intense.
   - ideas: 8-15 concrete assignments. Each has a title, format, pillar, description (what happens on screen or on the slides, concrete enough to shoot from), reasoning (which winner or gap it builds on), modeledOn (0-2 shortcodes whose skeleton it borrows) and a dayOffset spread at the cadence.
   - notes: up to 4 things worth flagging.
7. **Save it.** save_content_plan with startDate = day 0. The ideas land as idea cards with dates. Give the user the url.
8. **Offer the next step:** remix the 2-3 strongest ideas into scripts (remix skill) or carousels (carousel skill).

Defaults, not laws - override them with reasons: rotate pillars and formats, and never put two near-identical ideas back to back; double down on the creator's own winners before inventing; borrow skeletons, never topics and scripts verbatim; keep about one idea in seven as a wildcard; a pillar that cannot produce ten ideas in ten minutes is too vague.

## On a free account

- Steps 2 and 4 draw on the monthly allowances (30 Instagram lookups, 3 new watches). Prefer cached watches, pick the 1-3 posts that teach the most, and say so when you skip the rest.
- Building the inspiration list in bulk is a paid feature (see the discovery skill). With a thin list, ask the user for up to 5 accounts they admire and add them with add_inspiration_accounts.
- If a call answers upgrade_required, give the user its link once and finish the plan with what you have.
