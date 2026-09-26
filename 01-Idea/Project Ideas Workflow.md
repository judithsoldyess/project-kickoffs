# Project Ideas Workflow

For teams that don't have a project idea yet, or have a few and can't pick. Finds where the team's interests overlap and suggests buildable ideas. Writes `01-Idea/Idea.md`.

Already have an idea? Skip to **02-Pitch**.

## What good looks like
- [ ] Every team member's interests are captured (or marked `(skipped)`).
- [ ] 5–8 ideas, each with a one-sentence description, a specific target user, and one core v1 feature.
- [ ] Every idea is labelled `(suggested — not yet agreed)` until the team picks.
- [ ] Each idea fits the team's stack and deadline from `Team.md`. No idea needs a different stack than the one they chose (if the stack is "not decided", say what each idea would need).
- [ ] No idea needs heavy third-party infrastructure, is too broad to finish by the deadline, or is a straight clone with no twist.
- [ ] Exactly one idea is marked `(team decision)`, in the team's own words.

## IN
- `Team.md` — members, stack, deadline. If missing: "`Team.md` comes from **Start Here**. Want to run that first, or just tell me who's on the team and your deadline?"
- If `01-Idea/Idea.md` already exists, see **Re-running this step**.

## Process
1. Read `Team.md`. Say who you see on the team and the deadline, in one line.
2. Ask one question at a time:
   a. "What topics interest each of you? For example fitness, money, school, food, travel, games, a hobby. A few words per person is plenty."
   b. "What frustrates any of you day to day that a simple app could fix?"
   c. "Is there an idea any of you are already leaning toward? I'll include it in the options." (They can skip.)
   d. Only if `Team.md` doesn't say: "Are you building frontend only, or full-stack (a front end plus a server and database)?"
3. Find the overlap. Say in one or two lines where the team's interests meet ("Three of you mentioned food, and two mentioned budgeting").
4. Generate 5–8 ideas. For each:
   - **Name** — one-sentence description
   - **For:** a specific target user (not "everyone" or "users")
   - **Core v1 feature:** the one thing it must do on day one
   - **Why it fits your team:** the overlap it comes from
   - **Needs:** any outside service or API, or "nothing extra"
   - `(suggested — not yet agreed)`

   Include any idea the team said they were leaning toward (marked as theirs). Avoid ideas that need complex third-party infrastructure, need a different stack than the team chose, are too broad to finish by the deadline, or clone an existing app with no twist. If an idea needs a third-party API (an outside service your app calls for data, like weather or maps), say so under **Needs**.
5. [CHECKPOINT] Ask: "Which one does your team want to go with? You can also combine two, or change one." Wait for the team's answer. Don't pick for them. If they ask for your opinion, give one recommendation with one reason, still labelled as a suggestion.
6. Restate the chosen idea in the team's words and ask them to confirm.
7. Write `01-Idea/Idea.md` (standing rules 2 and 3).

## OUT
`01-Idea/Idea.md`:

```
# Idea — [team name]

_Last updated: YYYY-MM-DD_

## Our idea (team decision)
**[Name]** — [one sentence, in the team's words]
- For: [target user]
- Core v1 feature: [...]
- Why it fits: [...]
- Needs: [...]
- Came from: [idea number(s) below, combined or changed how]

## Team interests
- [Name]: [...]
- Frustrations mentioned: [...]

## Other ideas we considered (suggested — not yet agreed)
1. **[Name]** — [description]. For: [...]. Core v1 feature: [...]. Fits: [...]. Needs: [...].
2. ...
```

## Re-running this step
If `01-Idea/Idea.md` exists, show the chosen idea and ask: "Do you want to change your idea, get more options, or leave it?" Snapshot to `_history/01-Idea/Idea-YYYY-MM-DD-HHMM.md` before changing anything. If the idea changes and later steps already have files, tell the student which ones are now out of date (for example `Pitch.md`, `Features.md`) and suggest re-running them.

## Finish
- "I saved `01-Idea/Idea.md` and read it back."
- "Open it and check the idea is in your words."
- "Next: **02-Pitch**, to turn this idea into an elevator pitch."
