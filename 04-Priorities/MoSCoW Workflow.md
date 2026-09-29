# MoSCoW Workflow

Sorts the feature list into four tiers so the team knows what to build first. The team places every feature first; the AI only suggests moves afterwards, with reasons. Writes `04-Priorities/MoSCoW.md`.

**MoSCoW** stands for:
- **Must have** — the app doesn't work without it.
- **Should have** — important, but the app still works without it.
- **Could have** — nice if there's time.
- **Won't have (this time)** — deliberately left out of this version. Not forgotten, just not now.

## Opener
Cover, in a few short lines and your own words:
- **What:** your team sorts every feature into Must, Should, Could or Won't.
- **Why:** you can't build everything by your deadline. Deciding now what the app can't work without keeps the team building the right things first, and gives you a clear line when time runs short.
- **What I'll ask:** first, your team places every feature, using a sorter page with a button for each tier. Then, if you want, I'll suggest a few moves with a reason for each, and you decide.
- **What you'll get:** `MoSCoW.md`, your priorities with who decided each one.
- **Next:** 05-Breakdown splits your Musts into tasks you can build.

## What good looks like
- [ ] Every feature from the input list (not counting tech-stack cards) has exactly one tier. Features that landed in Won't only because nobody mentioned them were confirmed by the team.
- [ ] The team placed the features before the AI suggested any moves in this step (the list shown for placement had no suggested tiers), using `sorter.html` or a grouped one-per-line list.
- [ ] Before suggesting moves, the AI checked the placement against `Idea.md`'s core v1 feature, the pitch's main benefit, `Team.md`'s course requirements, and whether any Must depends on a lower-tier feature, and said what it found.
- [ ] Every AI-suggested move has a one-line reason, and the team accepted or rejected each one.
- [ ] The `Decided by` column is accurate: `team` for the team's placement, `team (accepted suggestion)` where they took a suggestion.
- [ ] Tech-stack cards (a database, framework or outside service instead of something a user does) are flagged and moved to a separate list, not tiered.
- [ ] If there are more than about 10 Musts, the team was warned with their deadline, and it's their call. The final Must count was stated after any suggestions.

## IN
- `03-Features/Features.md`. Or a pasted list, or a **photo of the workshop sticky-note board** (you can read images; check the `workshop/` folder and `Team.md`). If none of these: "Your feature list comes from **03-Features**. Want to run that, paste a list, or share a photo of your board?"
- `Team.md` for the deadline (used in the Must warning) and course requirements.
- `01-Idea/Idea.md` (core v1 feature) and `02-Pitch/Pitch.md` (main benefit), for the checks in step 6.
- `04-Priorities/sorter-template.html` (part of the kit): the sorter page you'll fill in.
- If `04-Priorities/MoSCoW.md` already exists, see **Re-running this step**.

## Process
1. Give the opener (standing rule 1). Read the input. If it's a photo, list what you read and ask: "Did I read every card correctly?" [CHECKPOINT]
   **If there's both a feature list and a board photo:** match them up first. Show three short lists: cards that match a feature ("'Share trip' → #15 Share a trip link"), cards with no matching feature, and features with no card. Ask one question at a time: whether to add the unmatched cards as features, and, where a card could match two features, which one it means. If the board already has tiers on it, say: "Your board already has tiers. I'll use them as your team's placement, and you can change any." Then make the sorter (step 3) with **only the features that had no card**, and say which features the board already placed. Then go to step 4.
2. **Flag tech-stack cards.** (Do this whenever one comes up, even mid-placement.) Any card that names a technology instead of something a user does ("Firebase", "REST API", "Gemini integration", "Postgres") is not a feature. Say: "'[card]' is a technical component, not something a user does, so it doesn't get a tier. I'll keep it in a separate list, and it'll show up in the Technical Considerations of the user stories that use it in step 06." Ask them to confirm once for all flagged cards.
3. Explain MoSCoW in two lines (definitions above), then let the team place features themselves, **without** any tiers shown. Don't suggest tiers while they're placing. If `Features.md` has suggested tiers from step 03, leave them out.

   **Make the sorter.** Copy `04-Priorities/sorter-template.html` to `04-Priorities/sorter.html` and replace only the JSON inside `<script id="features">` with the team's features: `{"product": "…", "made": "YYYY-MM-DD HH:MM", "areas": [{"area": "Core", "items": [{"n": 1, "name": "…", "desc": "…"}]}]}`, using the numbers, names, one-line descriptions and areas from `Features.md` (leave out tech-stack items). For a `(future)` item add `"future": true`. Set `"made"` to today's date and time. Write it as valid JSON (escape quotes in names, and write every `<` as `\u003c` so a name like "</script>" can't break the page), read it back, and don't change anything else in the file. Then say: "Double-click `04-Priorities/sorter.html` to open it in your browser. Tap M, S, C or W for each feature. When you're done, press **Copy our placement** and paste it here." If your chat can show interactive widgets, you may show the same sorter in the chat instead, with the same buttons, colours and copy/send step.

   Anything the sorter lists under **Not placed** counts as Won't until the team confirms it at the step 4 checkpoint.

   **If they can't use the sorter**, show the list grouped by area, one feature per line (standing rule 5), and ask for their Musts first, then Shoulds, then Coulds, one tier per message. Anything not mentioned goes to Won't. Never show the list as one block of text.
4. [CHECKPOINT] "This is what your team will build first, so let's make sure it's right." Show the placement as four headings (Must, Should, Could, Won't) with one feature per line under each, never packed into a table (standing rule 5), and ask: "Is this your team's placement?" Then, as its own question, list any features that ended up in Won't only because nobody placed them: "These landed in Won't because nobody placed them. Anything that should be higher?"
5. **Must check.** Count the Musts. Warn once per run, whenever the count is over about 10 and you haven't warned yet (after placement, after suggestions, or after a re-run change): "That's [N] Musts. That's a lot for [deadline from Team.md]. Every Must has to work before you demo. Do you want to move any down to Should?" Don't block. If they keep them, move on. Moves the team makes after this warning are `Decided by: team`.
6. **Expert checks, then suggestions.** First, check the placement yourself (standing rule 4):
   - Is `Idea.md`'s core v1 feature a Must? (No `Idea.md`? Use the `_Idea:_` line in `Pitch.md`.) If not, does the team mean to change v1? (If they do, that's a real decision: offer to update `Idea.md`, standing rule 12.)
   - Does the pitch's main benefit depend on a feature that isn't a Must?
   - Does any Must depend on a Should or Could, or any Should on a Could (it can't work until that's built too)?
   - Is any `(future)` item placed above Won't? That changes v1: confirm it with the team, and offer to update the files that parked it (standing rule 12).
   - Does the placement meet `Team.md`'s course requirements (login, number of APIs)? If a requirement needs a feature that isn't on the list at all, suggest adding it (the team decides) and offer to update `Features.md`.
   - Does any Must depend on data or a service the team may not have (exact measurements, forecasts)?
   Tell the team in plain language what you checked and what you found. Then ask: "Want me to suggest moves based on this? I'll give a reason for each, and you decide." If yes, suggest moves one at a time, each with a one-line reason (for example, "Move 'Password reset' to Must: users who forget their password can't get back in"). Wait for accept or reject on each before the next. Keep suggestions to the ones that matter most (usually 3–6). Afterwards, say the new Must count in one line ("You now have 12 Musts"). No second warning.
7. Write `04-Priorities/MoSCoW.md` (standing rules 7 and 8).

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

## Parked for later
- [...]

## Notes
- Placed by the team before any AI suggestions: yes
- Checks done: [core v1, pitch benefit, dependencies, course requirements, data] — [what was found]
- [Must count warning, if given, and what the team decided]
```

## Re-running this step
Scope changes during a project; that's normal. If `MoSCoW.md` exists, show the tier counts and ask (you can regenerate `sorter.html` with the current tiers left blank if they want to re-sort): "Do you want to move some features, add new ones, or redo the whole thing?" Snapshot to `_history/04-Priorities/MoSCoW-YYYY-MM-DD-HHMM.md` first. After changes, say the new Must count, which features changed tier, and every later file that already exists and is now out of date (`Breakdown.md`, `user-stories.md`, the board export and any GitHub issues or Trello cards already created, `07-Prototype/` files, and the copies in your project repo if `Team.md` lists them). Suggest re-running 05 → 06 → 07 for the changed features.

## Finish
- "I saved `04-Priorities/MoSCoW.md` and read it back."
- "Open it and check every tier is the one your team agreed."
- "Next: **05-Breakdown**, to split your features into pieces you can each build in one sitting."
