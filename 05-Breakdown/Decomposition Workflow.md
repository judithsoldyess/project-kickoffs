# Decomposition Workflow

Breaks features into small, concrete pieces. Each piece is something one person could build in a single focused session of 2–4 hours. Writes `05-Breakdown/Breakdown.md`.

**Decomposition** just means splitting something big into smaller parts.

## What good looks like
- [ ] The team chose which features to break down (default: all Musts first).
- [ ] Every piece fits one focused 2–4 hour session. Smaller pieces the team chose to keep separate are marked `(small)`.
- [ ] Every piece is concrete. "Login form that shows an error if the email is empty", not "implement auth".
- [ ] Pieces are in a sensible build order inside each feature, with anything that must come first noted.
- [ ] Grouped by tier, then by feature, with any project setup under **Setup** and features that live inside others marked "Built into".
- [ ] Pieces the AI proposed stay `(suggested — not yet agreed)` until the team confirms the feature's list.

## IN
- `04-Priorities/MoSCoW.md` (which features and tiers). If missing: "Your tiers come from **04-Priorities**. Want to run that, or paste your Must list here?"
- `Team.md` (stack, so pieces use the right words: "React component", "Django view", etc.). If part of the stack says "not decided", ask once whether it's been decided (standing rule 9).
- If `05-Breakdown/Breakdown.md` already exists, see **Re-running this step**.

## Process
1. Read `MoSCoW.md`. First, list any **setup** the team needs before any feature works (creating the project, connecting the database, the first deploy). These go under `## Setup` at the top, not under a feature. [CHECKPOINT] Show the Setup pieces and ask: "Anything missing here, like a first deploy?" Mark them `(team decision)` once agreed. Then say: "You have [N] Musts, [N] Shoulds, [N] Coulds." Ask: "Want to start with all your Musts? That's what I'd recommend." The team can pick any features instead.
2. For each chosen feature, one at a time:
   a. Split it into pieces. Each piece is one line, written as a concrete task someone could start right now. Good: "Sign-up form with email and password fields that shows an error if either is empty." Bad: "Build sign-up."
   b. Keep every piece to about 2–4 hours of work for one person. If a piece feels bigger, split it again. If it's tiny (under an hour), suggest merging it with a neighbour **in the same feature**; if the team wants to keep it separate, that's their call, so mark it `(small)`. A feature can be a single piece; if that one piece is under an hour, leave it as it is and mark it `(small)`.
   b2. Anything the team has never set up before (real-time updates, file uploads, sending email, a new outside API) almost always takes longer than it looks. Split it into "set up and prove it works" and "use it for the feature".
   c. Include the unglamorous pieces: the empty screen when there's no data yet, what happens when a form is filled in wrong, what happens when the network fails. These are where most of the real work lives.
   d. Put the pieces in build order. If one piece needs another first, note `needs: 2` (same feature) or `needs: [Feature name] 3` (another feature).
   e. Use the team's stack from `Team.md` in the wording where it helps.
   e2. If a feature is really built inside other features (like "friendly error messages"), don't invent pieces for it: write `Built into: [features]`.
   e3. If the team merges two features into one breakdown, name both in the heading.
   f. [CHECKPOINT] Show the pieces for this feature and ask: "Does this breakdown look right? Anything to split, merge or cut?" Apply edits. Mark the feature's pieces `(team decision)` once they agree.
3. When all Musts are done, ask: "Want to break down your Shoulds too?" Then the same for Coulds. Only do Won'ts if they ask.
4. Write `05-Breakdown/Breakdown.md` (standing rules 2 and 3). You can save after each tier so work isn't lost.

## OUT
`05-Breakdown/Breakdown.md`:

```
# Breakdown — [product name]

_Last updated: YYYY-MM-DD_
_Each piece is one focused session (2–4 hours) for one person._

## Setup (before any feature)
1. [e.g. Create the project and deploy a blank page]

## Must

### [Feature name] (team decision)
1. [Concrete piece]
2. [Concrete piece] — needs: 1
3. [Empty state / error piece]

### [Feature A] + [Feature B] (team decision)
1. ...

### [Feature name]
Built into: [Feature], [Feature]

### [Feature name] (suggested — not yet agreed)
1. ...

## Should
...

## Could
...

## Not broken down yet
- [Feature] ([tier])
```

## Re-running this step
If `Breakdown.md` exists, list which features are already broken down and which aren't. Ask: "Do you want to break down more features, change an existing breakdown, or start over?" Snapshot to `_history/05-Breakdown/Breakdown-YYYY-MM-DD-HHMM.md` first. If the Setup section is still `(suggested — not yet agreed)`, ask the Setup checkpoint question first. If `MoSCoW.md` changed since the last run (a feature moved tier or was removed), point that out and move its section to match.

## Finish
- "I saved `05-Breakdown/Breakdown.md` and read it back."
- "Open it and pick one piece: could someone on your team start it tomorrow morning without asking a question? If not, tell me and we'll make it clearer."
- "Next: **06-Stories**, to turn these into user stories your team builds from."
