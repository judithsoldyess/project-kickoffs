# MoSCoW Workflow

Sorts the feature list into four tiers so the team knows what to build first. The team places every feature first; the AI only suggests moves afterwards, with reasons. Writes `04-Priorities/MoSCoW.md`.

**MoSCoW** stands for:
- **Must have** — the app doesn't work without it.
- **Should have** — important, but the app still works without it.
- **Could have** — nice if there's time.
- **Won't have (this time)** — deliberately left out of this version. Not forgotten, just not now.

## What good looks like
- [ ] Every feature from the input list (not counting tech-stack cards) has exactly one tier. Features that landed in Won't only because nobody mentioned them were confirmed by the team.
- [ ] The team placed the features before the AI suggested any moves in this step (the list shown for placement had no suggested tiers).
- [ ] Every AI-suggested move has a one-line reason, and the team accepted or rejected each one.
- [ ] The `Decided by` column is accurate: `team` for the team's placement, `team (accepted suggestion)` where they took a suggestion.
- [ ] Tech-stack cards (a database, framework or outside service instead of something a user does) are flagged and moved to a separate list, not tiered.
- [ ] If there are more than about 10 Musts, the team was warned with their deadline, and it's their call. The final Must count was stated after any suggestions.

## IN
- `03-Features/Features.md`. Or a pasted list, or a **photo of the workshop sticky-note board** (you can read images; check the `workshop/` folder and `Team.md`). If none of these: "Your feature list comes from **03-Features**. Want to run that, paste a list, or share a photo of your board?"
- `Team.md` for the deadline (used in the Must warning).
- If `04-Priorities/MoSCoW.md` already exists, see **Re-running this step**.

## Process
1. Read the input. If it's a photo, list what you read and ask: "Did I read every card correctly?" [CHECKPOINT]
   **If there's both a feature list and a board photo:** match them up first. Show three short lists: cards that match a feature ("'Share trip' → #15 Share a trip link"), cards with no matching feature, and features with no card. Ask one question at a time: whether to add the unmatched cards as features, and, where a card could match two features, which one it means. If the board already has tiers on it, say: "Your board already has tiers. I'll use them as your team's placement, and you can change any." Then ask the team to place only the features that had no card (as in step 3: chunks of about 10, no tiers shown). Then go to step 4.
2. **Flag tech-stack cards.** (Do this whenever one comes up, even mid-placement.) Any card that names a technology instead of something a user does ("Firebase", "REST API", "Gemini integration", "Postgres") is not a feature. Say: "'[card]' is a technical component, not something a user does, so it doesn't get a tier. I'll keep it in a separate list, and it'll show up in the Technical Considerations of the user stories that use it in step 06." Ask them to confirm once for all flagged cards.
3. Explain MoSCoW in two lines (definitions above), then ask the team to place features themselves. Offer two ways:
   - "Tell me your Musts first, then your Shoulds, then your Coulds. Anything you don't mention goes in Won't. You can also share a photo of your board if you've already done this."
   - Or go through the list in chunks of about 10 and ask for the tier of each.

   Show the list **without** any tiers. Don't suggest tiers while they're placing. If `Features.md` has suggested tiers from step 03, leave them out of the list you show.
4. [CHECKPOINT] Show the team's placement as a table and ask: "Is this your team's placement?" List separately any features that ended up in Won't only because nobody mentioned them: "These landed in Won't because nobody named them. Is that right?"
5. **Must check.** Count the Musts. If more than about 10, say once: "That's [N] Musts. That's a lot for [deadline from Team.md]. Every Must has to work before you demo. Do you want to move any down to Should?" Don't block. If they keep them, move on. Moves the team makes after this warning are `Decided by: team`.
6. **Suggestions (optional).** Ask: "Want me to suggest any moves? I'll give a reason for each, and you decide." If yes, suggest moves one at a time, each with a one-line reason (for example, "Move 'Password reset' to Must: users who forget their password can't get back in"). Wait for accept or reject on each before the next. Keep suggestions to the ones that matter most (usually 3–6). Afterwards, say the new Must count in one line ("You now have 12 Musts"). No second warning.
7. Write `04-Priorities/MoSCoW.md` (standing rules 2 and 3).

## OUT
`04-Priorities/MoSCoW.md`:

```
# MoSCoW — [product name]

_Last updated: YYYY-MM-DD_
_Build order: Must → Should → Could. Won't is out of scope unless we say otherwise._

| # | Feature | Tier | Decided by | Reason |
|---|---|---|---|---|
| 1 | Create an account | Must | team | Everything else is saved per user |
| 2 | Password reset | Must | team (accepted suggestion) | Users who forget can't get back in |
| 3 | Dark mode | Could | team | |
| ... | | | | |

## Tech-stack items (not features)
These show up in Technical Considerations (or the Setup checklist) in step 06.
- [Firebase] — [what it's for]

## Suggestions we turned down
- [Feature]: suggested [tier] because [...] — team kept it at [tier]

## Notes
- Placed by the team before any AI suggestions: yes
- [Must count warning, if given, and what the team decided]
```

## Re-running this step
Scope changes during a project; that's normal. If `MoSCoW.md` exists, show the tier counts and ask: "Do you want to move some features, add new ones, or redo the whole thing?" Snapshot to `_history/04-Priorities/MoSCoW-YYYY-MM-DD-HHMM.md` first. After changes, say the new Must count, which features changed tier, and every later file that already exists and is now out of date (`Breakdown.md`, `user-stories.md`, the board export and any GitHub issues or Trello cards already created, `07-Prototype/` files, and the copies in your project repo if `Team.md` lists them). Suggest re-running 05 → 06 → 07 for the changed features.

## Finish
- "I saved `04-Priorities/MoSCoW.md` and read it back."
- "Open it and check every tier is the one your team agreed."
- "Next: **05-Breakdown**, to split your features into pieces you can each build in one sitting."
