# Project Ideas Workflow

For teams that don't have a project idea yet, or have a few and can't pick. Finds what the team cares about and suggests buildable ideas. Writes `01-Idea/Idea.md`.

Already have an idea? Skip to **02-Pitch**.

## Opener
Cover, in a few short lines and your own words:
- **What:** we'll find a project idea your team is excited about and can actually finish.
- **Why:** a good idea is one you care about *and* can build by your deadline. It's easier to pick well now than to change direction halfway through.
- **What I'll ask:** what topics interest your team, what frustrates you day to day, and whether you're already leaning toward something. Then I'll suggest a handful of ideas and you pick one (or combine them).
- **What you'll get:** `Idea.md`, with your chosen idea, who it's for, and the one thing it has to do on day one.
- **Next:** 02-Pitch turns the idea into a short pitch.

## What good looks like
- [ ] The team's interests are captured (as a team; not per person).
- [ ] 5–8 ideas, each with a one-sentence description, a specific target user, and one core v1 feature.
- [ ] Every idea is labelled `(suggested — not yet agreed)` until the team picks.
- [ ] Each idea fits the team's stack, course requirements and deadline from `Team.md`. No idea needs a different stack than the one they chose (if the stack is "not decided", say what each idea would need).
- [ ] No idea needs heavy third-party infrastructure, is too broad to finish by the deadline, or is a straight clone with no twist.
- [ ] Exactly one idea is marked `(team decision)`, in the team's own words, with its core v1 feature confirmed by the team.

## IN
- `Team.md` — stack, course requirements, deadline. If missing: "`Team.md` comes from **Start Here**. Want to run that first, or just tell me your stack and deadline?"
- If `01-Idea/Idea.md` already exists, see **Re-running this step**.

## Process
1. Give the opener (standing rule 1). Say in one line what you read in `Team.md` (stack and deadline).
2. Ask one question at a time, skipping any that's already answered:
   a. "What topics interest your team? For example fitness, money, school, food, travel, games, a hobby. A few words is plenty."
   b. "What frustrates any of you day to day that a simple app could fix?"
   c. "Is there an idea you're already leaning toward? I'll include it in the options." (Why: so your own idea gets a fair shot alongside mine.)
   d. Only if `Team.md` doesn't say: "Are you building frontend only, or full-stack (a front end plus a server and database)?"

   **If an idea comes up before question c** (they describe an app instead of interests), stop and ask: "Sounds like you already have an idea. Want me to suggest some variations on it here, or go straight to **02-Pitch**? Variations can show you a sharper version before you commit." If they want variations, ask 2b only (it shapes the variations), skip 2c, and build the ideas in step 4 around theirs.
3. Say in one or two lines what you heard (the topics and frustrations that stood out).
4. Generate 5–8 ideas. Show each one as a short block (standing rule 5):
   - **Name** — one-sentence description
   - **For:** a specific target user (not "everyone" or "users")
   - **Core v1 feature:** the one thing it must do on day one
   - **Why it fits your team:** what it comes from
   - **Needs:** any outside service or API, or "nothing extra"
   - `(suggested — not yet agreed)`

   Include any idea the team said they were leaning toward (marked as theirs). Check each idea yourself (standing rule 4) against the stack, course requirements and deadline. Leave out ideas that need complex third-party infrastructure, need a different stack than the team chose, are too broad to finish by the deadline, or clone an existing app with no twist.
5. [CHECKPOINT] "You'll build one idea, so pick the one your team is most excited about. You can also combine two, or change one. Which one?" Wait for the team's answer. Don't pick for them. If they ask for your opinion, give one recommendation with one reason, still labelled as a suggestion.
   - **If they want everything** ("we like all of them"): say that's a good sign, and explain that by the deadline they can build one small version really well. Everything else isn't lost: it can become a feature in 03-Features and get prioritized in 04. Then ask: "What should the app do for someone first?" Build the chosen idea around that answer, and add the core feature of each other idea they liked to **Parked for later** (labelled `(from idea N)`), so 03 picks them up.
   - **If they combine ideas:** ask separately for the core v1 feature: "Of everything in the combined idea, what's the one thing it must do on day one?" Offer a suggestion if they want one, labelled.
6. Restate the chosen idea and its core v1 feature in the team's words and ask them to confirm. Anything they said was for later goes under **Parked for later**.
7. Write `01-Idea/Idea.md` (standing rules 7 and 8).

## OUT
`01-Idea/Idea.md`:

```
# Idea — [project name, or "name not decided yet"]

_Last updated: YYYY-MM-DD_

## Our idea (team decision)
**[Name]** — [one sentence, in the team's words]
- For: [target user]
- Core v1 feature: [...] (team decision)
- Why it fits: [...]
- Needs: [...]
- Came from: [idea number(s) below, combined or changed how]

## Team interests
- Topics: [...]
- Frustrations mentioned: [...]

## Parked for later
- [ideas the team said weren't for this version]

## Other ideas we considered (suggested — not yet agreed)
1. **[Name]** — [description]. For: [...]. Core v1 feature: [...]. Fits: [...]. Needs: [...].
2. ...
```

## Re-running this step
If `01-Idea/Idea.md` exists, show the chosen idea and ask: "Do you want to change your idea, get more options, or leave it?" Snapshot to `_history/01-Idea/Idea-YYYY-MM-DD-HHMM.md` before changing anything. If the idea changes and later steps already have files, name each one that's now out of date (standing rule 12).

## Finish
- "I saved `01-Idea/Idea.md` and read it back."
- "Open it and check the idea and its core v1 feature are in your words."
- "Next: **02-Pitch**, to turn this idea into an elevator pitch."
