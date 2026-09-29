# Feature Brainstorm Workflow

Brainstorms about 30 possible features for the app, so the team has a wide list to prioritize in step 04. Writes `03-Features/Features.md`.

This is a brainstorm, not a plan. You won't build all of these.

## Opener
Cover, in a few short lines and your own words:
- **What:** we'll list everything your app *could* do, about 30 ideas.
- **Why:** it's much easier to choose what to build when you can see all the options side by side. Nothing here is a commitment.
- **What I'll ask:** first, whether there's anything you already know you want. Then I'll show the list and ask what to remove, add or reword.
- **What you'll get:** `Features.md`, grouped by area.
- **Next:** 04-Priorities, where your team sorts the list into Must, Should, Could and Won't.

## What good looks like
- [ ] About 30 features from the AI (25–35 is fine; the team's own additions don't count against this), each as **name — one-line description**.
- [ ] Grouped by area: core, accounts, sharing, admin, polish, onboarding and errors (skip an area that doesn't fit, and say why).
- [ ] A mix of obvious features and a few creative ones.
- [ ] Features are things a user does or sees. Tech-stack items ("React", "Postgres", "REST API") are listed separately under **Tech notes**, not numbered as features.
- [ ] Suggested tiers appear only if the team asked for them, each labelled `(suggested tier: Must/Should/Could)`; nothing is presented as decided.
- [ ] Features already named in earlier files (Idea.md, Pitch.md, any Parked for later) are on the list.
- [ ] Likely overlaps, including in the team's own additions, were pointed out and the team decided what to do with each.

## IN
- `02-Pitch/Pitch.md` (the pitch drives the brainstorm). If missing: "Your pitch comes from **02-Pitch**. Want to run that, or paste your pitch here?"
- `01-Idea/Idea.md` and the **Parked for later** sections of earlier files: features the team already named.
- `Team.md` (stack, course requirements and deadline, so suggestions stay realistic).
- If `03-Features/Features.md` already exists, see **Re-running this step**.

## Process
1. Give the opener (standing rule 1). Read `Pitch.md` and restate the pitch in one line. Then list, one per line, the features the team already named in earlier files (the core v1 feature, things in the pitch's benefit and difference, Parked for later) and say: "These are on the list already, from what you told me earlier." Ask: "Anything else you already know you want on the list?" (One question. They can skip.) If they name a technology ("Supabase login"), turn it into the user feature it enables and say so, as its own question: "You said Supabase: I'll list 'Log in with email' as the feature, and put Supabase under Tech notes. Sound right?" If it doesn't enable anything a user sees (a database, an API style), just list it under Tech notes.
2. Generate about 30 features, grouped by area:
   - **Core** — the main thing the app does
   - **Accounts** — sign up, log in, profiles (skip if the app has no accounts, and say so)
   - **Sharing** — social, sharing, collaboration (if it fits)
   - **Admin** — features for whoever runs the app (your team, or a moderator): managing content, simple stats. Only include this area if the app needs someone to manage content. (No accounts? Call it **Your data and stats**: what users can see about their own data.)
   - **Polish** — search, filters, notifications, dark mode
   - **Onboarding and errors** — first-time user experience, empty screens, what happens when something fails

   If `Team.md`'s course requirements need something (login, a number of outside APIs), make sure the list has features that meet them, and say which ones do.

   Format each as: `N. **Feature name** — one line on what the user can do.` Number across the whole list, not per group. Show it one feature per line under its area heading (standing rule 5).

   Don't add tiers by default: the team places features themselves in step 04, and seeing your tiers first tends to steer them. If the team asks for your view, add a suggested tier at the end of each line, `(suggested tier: Must)`, and say once: "These are my suggestions only. You'll decide the real tiers in step 04."
3. Mark everything the team already named `(team decision)`. If they call something "future" or "not for v1", keep it on the list with `(future)` at the end; 04 will treat it as a Won't candidate.
4. Say: **"Quick scan: remove any obvious duplicates before pasting. This list is yours to edit."**
5. Check the list yourself for likely overlaps (standing rule 4), including in anything the team added, and name them: "'Plant location' and 'Rooms' look like the same thing. Merge them, or keep both?" Ask about each one separately.
6. [CHECKPOINT] "This is the list your team will prioritize next, so it's worth a minute. What do you want to remove, add, or reword?" Apply their edits, and run the step-5 overlap check on anything they add before showing the list again. New features go at the end of their area with the next number; don't renumber. If they add a technology rather than a feature, say once that it isn't a feature and put it under Tech notes. If they still want it numbered, keep it in Tech notes and explain that steps 04 and 06 will use it from there; it won't get lost. Repeat until they say it's good.
7. Write `03-Features/Features.md` (standing rules 7 and 8).

## OUT
`03-Features/Features.md`:

```
# Features — [product name]

_Last updated: YYYY-MM-DD_
_Brainstorm list. Nothing here is prioritized yet; that's step 04._
_The team reviewed this list; features the team named themselves are marked (team decision)._

## Core
1. **[Feature]** — [one line]   ← add "(suggested tier: …)" only if the team asked
2. ...

## Accounts
...

## Sharing
...

## Admin
...

## Polish
...

## Onboarding and errors
...

## Tech notes (for step 04, not features)
- [technology] — [what it's for]

## Parked for later
- [carried from earlier files, plus anything new]

## Edited by the team
- Removed: [...]
- Added: [...] (team decision)
```

## Re-running this step
If `Features.md` exists, show the count per area and ask: "Do you want to add more ideas, edit the list, or start over?" Snapshot to `_history/03-Features/Features-YYYY-MM-DD-HHMM.md` first. When adding, continue the numbering and don't repeat features already listed.

## Finish
- "I saved `03-Features/Features.md` and read it back."
- "Open it and scan it one more time. If your team has a sticky-note board from the workshop, compare them."
- "Next: **04-Priorities**, where your team sorts these into Must, Should, Could and Won't."
