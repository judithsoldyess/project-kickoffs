# Feature Brainstorm Workflow

Brainstorms about 30 possible features for the app, so the team has a wide list to prioritize in step 04. Writes `03-Features/Features.md`.

This is a brainstorm, not a plan. You won't build all of these.

## What good looks like
- [ ] About 30 features (25–35 is fine), each as **name — one-line description**.
- [ ] Grouped by area: core, accounts, sharing, admin, polish, onboarding and errors (skip an area that doesn't fit, and say why).
- [ ] A mix of obvious features and a few creative ones.
- [ ] Features are things a user does or sees. Tech-stack items ("React", "Postgres", "REST API") are listed separately under **Tech notes**, not numbered as features.
- [ ] Suggested tiers appear only if the team asked for them, each labelled `(suggested tier: Must/Should/Could)`; nothing is presented as decided.
- [ ] The team did a quick duplicate scan and edited the list before it was saved.

## IN
- `02-Pitch/Pitch.md` (the pitch drives the brainstorm). If missing: "Your pitch comes from **02-Pitch**. Want to run that, or paste your pitch here?"
- `Team.md` (stack and deadline, so suggestions stay realistic).
- If `03-Features/Features.md` already exists, see **Re-running this step**.

## Process
1. Read `Pitch.md` and restate the pitch in one line. Ask: "Anything you already know you want on the list?" (One question. They can skip.) If they name a technology ("Supabase login"), turn it into the user feature it enables and say so, as its own question: "You said Supabase: I'll list 'Log in with email' as the feature, and put Supabase under Tech notes. Sound right?" If it doesn't enable anything a user sees (a database, an API style), just list it under Tech notes.
2. Generate about 30 features, grouped by area:
   - **Core** — the main thing the app does
   - **Accounts** — sign up, log in, profiles (skip if the app has no accounts, and say so)
   - **Sharing** — social, sharing, collaboration (if it fits)
   - **Admin** — managing content, simple stats (no accounts? call this area **Your data and stats**)
   - **Polish** — search, filters, notifications, dark mode
   - **Onboarding and errors** — first-time user experience, empty screens, what happens when something fails

   Format each as: `N. **Feature name** — one line on what the user can do.` Number across the whole list (1–30), not per group.

   Don't add tiers by default: the team places features themselves in step 04, and seeing your tiers first tends to steer them. If the team asks for your view, add a suggested tier at the end of each line, `(suggested tier: Must)`, and say once: "These are my suggestions only. You'll decide the real tiers in step 04."
3. Include anything the team said they already wanted, marked `(team decision)`.
4. Say: **"Quick scan: remove any obvious duplicates before pasting. This list is yours to edit."**
5. [CHECKPOINT] Ask: "What do you want to remove, add, or reword?" Apply their edits. If they add a technology rather than a feature, say once that it isn't a feature and put it under Tech notes. If they still want it numbered, keep it in Tech notes and explain that steps 04 and 06 will use it from there; it won't get lost. Repeat until they say it's good.
6. Write `03-Features/Features.md` (standing rules 2 and 3).

## OUT
`03-Features/Features.md`:

```
# Features — [product name]

_Last updated: YYYY-MM-DD_
_Brainstorm list. Nothing here is prioritized yet; that's step 04._

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
