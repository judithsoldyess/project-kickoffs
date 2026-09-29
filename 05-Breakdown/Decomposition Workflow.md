# Decomposition Workflow

Breaks each feature into small, concrete tasks, one feature at a time. Each task is something one person could build in a single focused session of 2–4 hours. Writes `05-Breakdown/Breakdown.md`.

**Decomposition** just means splitting something big into smaller parts.

**How this connects to step 06 (say this to the student in the opener, and keep to it):** each feature becomes a few tasks here. In step 06, up to 3 tasks become one user story, and each story becomes one card or issue on your board, with its tasks as a checklist on that card. A feature with more than 3 tasks becomes more than one story.

## Opener
Cover, in a few short lines and your own words:
- **What:** we'll take your Must features one at a time and split each one into small tasks (this is called decomposition), the size one person can build in an afternoon. We describe each feature by what someone can see or do, then list what has to be built to make that true.
- **Why:** "build the photo thing" is too big to start on. Small, concrete tasks are how a team divides the work, sees progress, and spots the hard parts early instead of the week before the demo.
- **What I'll ask:** for each feature, I'll show you what someone will be able to see or do once it's built, then the tasks to get there. You check the first part: is that what you want people to be able to do? The tasks and how long they take are my job, and I'll tell you if something looks risky. You don't need to know how to split things up; watching me do it is how you learn it.
- **What you'll get:** `Breakdown.md`, with every task saved.
- **Next:** in 06, up to 3 of these tasks at a time become a user story on your board.

## What good looks like
- [ ] The team chose which features to break down (default: all Musts first).
- [ ] Every feature starts with a **Once built:** line saying what a person can see or do when it's finished.
- [ ] Every task fits one focused 2–4 hour session (the AI judged this, not the student). Smaller tasks the team chose to keep separate are marked `(small)`.
- [ ] Every task is concrete. "Login form that shows an error if the email is empty", not "implement auth".
- [ ] Tasks are in a sensible build order inside each feature, with anything that must come first noted.
- [ ] Risky tasks (first-time setup, anything the pitch depends on that may not exist) are flagged with a plain-language heads-up.
- [ ] Grouped by tier, then by feature, with any project setup under **Setup**, features that live inside others marked "Built into", and shared work cross-referenced rather than merged.
- [ ] The finish says how many features became how many tasks, and where they're saved.
- [ ] Tasks the AI proposed stay `(suggested — not yet agreed)` until the team confirms that feature.

## IN
- `04-Priorities/MoSCoW.md` (which features and tiers). If missing: "Your tiers come from **04-Priorities**. Want to run that, or paste your Must list here?"
- `Team.md` (stack, so tasks use the right words: "React component", "Django view", etc.; course requirements). If part of the stack says "not decided", ask once whether it's been decided (standing rule 12).
- `02-Pitch/Pitch.md` (what the pitch promises, for the feasibility heads-ups).
- If `05-Breakdown/Breakdown.md` already exists, see **Re-running this step**.

## Process
1. Give the opener (standing rule 1), including how this connects to step 06.
2. **Setup.** List any setup the team needs before any feature works (creating the project, connecting the database, the first deploy). These go under `## Setup` at the top, not under a feature. Check the list yourself first (standing rule 4): it should cover everything your Musts need before they can work, given the stack and course requirements. [CHECKPOINT] "Before any feature works, someone has to set up the project. I've checked this covers what your Musts need. Is there anything your course or instructors require that I should add? 'Looks good' and 'not sure, keep going' are fine answers." Mark them `(team decision)` once agreed.
3. Say: "You have [N] Musts, [N] Shoulds, [N] Coulds." Ask: "Start with all [N] Musts, or pick different features? Musts first means the app works end to end soonest." Wait for the answer before showing the first feature.
4. **One feature at a time.** For each chosen feature, work it out first (a–f), then show it (g).
   a. Split it into tasks. Each task is one line, written as a concrete task someone could start right now. Where you can, say what it adds for the user, with technical detail after ("Results screen that shows the plant's problem and what to do — gets the answer from the diagnosis service"). Good: "Sign-up form with email and password fields that shows an error if either is empty." Bad: "Build sign-up."
   b. **Size them yourself** (standing rule 4). Keep every task to about 2–4 hours for one person. If a task is bigger, split it. If it's tiny (under an hour), merge it with a neighbour **in the same feature**; if the team wants to keep it separate, that's their call, so mark it `(small)`. A feature can be a single task; if that task is under an hour, leave it and mark it `(small)`.
   c. Anything the team has never set up before (real-time updates, file uploads, photos, sending email, a new outside API) almost always takes longer than it looks. Split it into "set up and prove it works" and "use it for the feature".
   d. Include the unglamorous tasks: the empty screen when there's no data yet, what happens when a form is filled in wrong, what happens when the network or an outside service fails. These are where most of the real work lives.
   e. Put the tasks in build order. If one needs another first, note `needs: 2` (same feature) or `needs: [Feature name] 3` (another feature). If a task needs a task from a feature that comes **later** in build order (creating an account needs part of log-in), move the shared part into the earlier feature instead. If two features share work, keep them as separate features and point to the shared task with `needs:`. Don't merge them into one heading.
   f. **Feasibility heads-up.** If the pitch promises something that depends on a risky task (no plant service gives "half a glass of water"; forecasting needs data the team won't have), say so as a heads-up from someone who's been there, and suggest a simpler way. If you propose a shortcut, say why it still works at scale ("a list of exceptions by plant family: 10–15 families cover thousands of plants, and everything else gets the default"). If a feature is really built inside other features (like "friendly error messages"), don't invent tasks for it: write `Built into: [features]`.
   g. [CHECKPOINT] Show it in exactly this shape, one feature per message:

      > **Must [N] of [M]: [Feature name]**
      > **Once built:** [what a person can see or do, in one plain sentence]
      > Tasks:
      > 1. [task]
      > 2. [task] — needs: 1
      > …
      > [any heads-up, in one or two lines]
      >
      > Does that sound right? Say yes, or tell me what you'd change.

      For the first feature only, add one line above the question: "The part to check is the Once built line: is that what you want someone to be able to do? The tasks are my job." "Yes", "not sure, keep going" and changes are all fine answers. Apply edits. Mark the feature's tasks `(team decision)` once they agree. If they say "not sure, keep going", mark it `(team said: not sure, keep going)` instead and say so, so step 06 knows it wasn't really agreed.

      For a feature that is **Built into** others, use the same shape but replace the tasks with: "**Built into:** [features] (no tasks of its own: it happens inside those)."
5. When all Musts are done, tell them: "You can stop here if you like. Step 06 can write stories for your Shoulds and Coulds straight from your priorities, without a breakdown. Or we can break down your Shoulds too." Then the same for Coulds if they continue. Only do Won'ts if they ask.
6. Write `05-Breakdown/Breakdown.md` (standing rules 7 and 8). You can save after each tier so work isn't lost.

## OUT
`05-Breakdown/Breakdown.md`:

```
# Breakdown — [product name]

_Last updated: YYYY-MM-DD_
_Each task is one focused session (2–4 hours) for one person. In step 06, up to 3 tasks become one user story._

## Setup (before any feature)
1. [e.g. Create the project and deploy a blank page]

## Must

### [Feature name] (team decision)
Once built: [what a person can see or do]
1. [Concrete task]
2. [Concrete task] — needs: 1
3. [Empty state / error task]
Heads-up: [risk, if any]

### [Feature name] (team decision)
Once built: [...]
1. [task] — needs: [Other feature] 2

### [Feature name]
Once built: [what a person can see or do]
Built into: [Feature], [Feature]

## Should
...

## Could
...

## Not broken down yet
- [Feature] ([tier])

## Open questions
- [things to check with instructors or the team, and what changes if the answer is yes]

## Parked for later
- [...]
```

## Re-running this step
If `Breakdown.md` exists, list which features are already broken down and which aren't. Ask: "Do you want to break down more features, change an existing breakdown, or start over?" Snapshot to `_history/05-Breakdown/Breakdown-YYYY-MM-DD-HHMM.md` first. If the Setup section is still `(suggested — not yet agreed)`, ask the Setup checkpoint question first. If `MoSCoW.md` changed since the last run (a feature moved tier or was removed), point that out and move its section to match. Name any stories or board cards now out of date (standing rule 12).

## Finish
- Show the work (standing rule 6): "[N] features became [N] tasks (plus [N] setup tasks), saved in `05-Breakdown/Breakdown.md`."
- "I saved it and read it back. Open it and pick one task: could someone on your team start it tomorrow morning without asking a question? If not, tell me and we'll make it clearer."
- "Next: **06-Stories**. Up to 3 of these tasks become one user story, and each story becomes a card on your board with its tasks as a checklist."
