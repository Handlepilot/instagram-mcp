---
name: discovery
description: Build an Instagram creator's watch-list of 20-30 competitor and inspiration accounts in HandlePilot - gather candidates widely, screen them in batches, judge them on their content, confirm by watching, then add them for the user to verify. Use when the user asks to find competitors, similar creators, accounts in their niche or accounts to learn from, or when the inspiration list is thin. Batch screening is on HandlePilot's paid plan.
---

# Finding inspiration accounts

Goal: 20-30 accounts the creator opens and thinks "this is my arena - I want to learn from this", added to their inspiration list for them to verify. A full run is a few hundred scans and up to 60-80 watches, a real share of the monthly allowance; a small niche needs less.

1. **Write the creator brief before any search.** Read get_creator_context and get_instagram_account on their own handle (posts: 24-36). Note for yourself, in 4-6 lines: who they are, what problem they solve and for whom, the audience's language, their angle (science-backed, spiritual, humorous...), the formats that work for them, and what would make an account wrong for them. Every judgement below is against this brief. Read list_inspiration_accounts too: accounts already there need no second look.

2. **Gather 100-300 candidate handles.** No single source finds the whole arena:
   - Keyword search: search_instagram kind "profiles" for 10-16 terms in the audience's language. Use the labels people put in their names and bios ("психолог", "нейропсихолог", "nutritionist"), not topic phrases. Each search returns a few dozen names.
   - Reels search: search_instagram kind "reels" on the niche's topics: whose content on the subject performs this month.
   - The web: search for rankings, "top accounts" lists, press, course rosters and podcast guests in the niche, in the audience's language and in English. The big players come from here; Instagram search mostly returns small accounts. Keep where you found each handle.
   - Leads: the creator's own related accounts (get_instagram_account), then the related and mentions lists on the cards you scan. Hop once from the best ones.
   - Global references: 3-5 accounts in another language whose formats the creator could borrow, often ones they already cite.
   Merge, lowercase and dedupe.

3. **Screen in batches.** scan_instagram_accounts, up to 20 handles a call, with workspace and language. Drop every account flagged not_found, private, small, inactive, adult, own_account or on_list, and wrong_language unless it is a global reference you chose. Never suggest an account flagged removed_by_user: the user threw it out. Send notScanned handles again.

4. **Judge on the cards,** which costs nothing: bio, newest captions, top posts, numbers. Keep an account only when its content is about the creator's subject, for a similar audience, and could teach them something: a format, a hook, an angle. Drop off-niche virality (an expert whose views come from dance trends), lifestyle diaries with a niche word in the bio, aggregators and repost pages, and inflated accounts (many followers, tiny views). Compare on views, never likes; likes are often hidden. Expect to keep a third or fewer.

5. **Watch to confirm.** For each account still in doubt, watch_video with detail "brief" on 2-3 posts: its top post and a typical recent one, because outliers are often off-topic. Use the default watch, not a question: it is cached, and the strategy and remix skills reuse it. Decide against the brief: same subject, same audience, something to learn? Skip the watch when the captions already settle it.

6. **Shape the list:** 20-30 accounts across tiers - a few niche leaders, mid-size accounts with high views per follower, 4-6 accounts near the creator's size that outperform them, 3-5 global format references. Prefer variety in what they teach over many copies of one kind of account. Rate each account's fit on the same scale HandlePilot's own discovery uses: 2 = same arena (same subject, same audience), 1 = adjacent, 0 = a reference only (a format worth borrowing, another language).

7. **Add the list right away:** add_inspiration_accounts with every account and its fit, in one call. HandlePilot scores each row against the whole list, and they arrive unverified. Give the user the url ("here is your list, have a look") with a few lines on what you kept and why, not a table to approve in chat. In the app they check the keepers and remove the rest; removed accounts are never suggested again.

8. **When the user tells you instead which to keep or drop,** call verify_inspiration_accounts for the keepers and remove_inspiration_account for the others. The accounts' posts refresh within a few minutes; list_top_content then shows the arena's best work for the strategy and remix skills.

## On a free account

scan_instagram_accounts is a paid-plan tool and answers upgrade_required on a free account. Tell the user once what it would do and give them the link. Then run a small version: up to 5 accounts per workspace, added by hand.

- Ask the user which accounts they already admire, and fill the gaps with a few search_instagram calls and the web.
- Check candidates with get_instagram_account. Searches and account lookups count against the 30 Instagram lookups a month, so check only the strongest few.
- Add at most 5 with add_inspiration_accounts.
