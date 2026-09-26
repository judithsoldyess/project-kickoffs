# Project Kickoff

A step-by-step kit that takes your team from "we have a project" to a prioritized feature list, user stories in build order, and a clickable prototype. You run it with an AI coding assistant. It asks one question at a time, your team makes the decisions, and every step saves a file you can open, share and change later.

There's nothing to install. This folder *is* the kit.

---

## How to open it

**With Claude Code**

Open a terminal, go to this folder, and start Claude Code:

```
cd "Project Kickoff"
claude
```

(Use the real path to wherever you unzipped it, for example `cd "Downloads/Project Kickoff"`.) Then type: **Start Here**.

**With another AI coding assistant** (Codex, Cursor, and others)

Open this folder in the tool. It reads `AGENTS.md`, which has the same rules. Then ask it to follow `Start Here.md`.

**No coding assistant?**

Open any workflow file, copy all of it, and paste it into a chat assistant (Claude, ChatGPT, or similar) with: "Follow these instructions with me." Save the files it gives you into the matching folder yourself.

Works the same on Mac, Windows and Linux.

---

## The steps

Run them in order. Each one reads the files the earlier steps wrote, so you don't repeat yourself. To start a step, say its name, for example **"Run 04-Priorities"**.

| Step | Reads (IN) | Writes (OUT) | Good looks like |
|---|---|---|---|
| **Start Here** | — | `Team.md` | Team, roles, one kit runner, stack, deadline, board |
| **01-Idea** | `Team.md` | `01-Idea/Idea.md` | 5–8 ideas from your shared interests; the team picked one |
| **02-Pitch** | `Idea.md` | `02-Pitch/Pitch.md` | A specific, speakable pitch plus a one-liner and a README blurb |
| **03-Features** | `Pitch.md` | `03-Features/Features.md` | About 30 features, grouped by area, duplicates removed |
| **04-Priorities** | `Features.md` (or a board photo) | `04-Priorities/MoSCoW.md` | Every feature in Must / Should / Could / Won't, placed by your team |
| **05-Breakdown** | `MoSCoW.md` | `05-Breakdown/Breakdown.md` | Each feature split into concrete 2–4 hour pieces |
| **06-Stories** | `Breakdown.md`, `MoSCoW.md`, `Team.md` | `06-Stories/user-stories.md` + GitHub and/or Trello export | Stories in build order, workshop format, tagged by tier |
| **07-Prototype** | `user-stories.md`, `Pitch.md`, `Team.md` | `07-Prototype/prototype.html`, `style-guide.html`, `screens.md` | A clickable prototype that opens with a double-click |

Already have an idea? Skip 01. Already have a feature list or a MoSCoW board from the workshop? Put a photo in a `workshop` folder inside the kit, then start at 04.

---

## How teams use it

- **Pair while you run it.** Sit together (or share a screen). The kit asks questions; your team answers.
- **One person runs the kit.** You'll name them in Start Here. They keep the files and share them with everyone (in your project repo, a shared drive, or your team chat). Two people running it separately ends up with two different versions of your plan.
- **You decide, the AI suggests.** Everything the AI proposes is marked `(suggested — not yet agreed)` until your team says yes. Your choices are marked `(team decision)`.
- **Skip anything.** Type **skip** on any question.

At the end of 06-Stories, the kit offers to copy `user-stories.md` into your project repo.

---

## Running a step again

Plans change. Run any step again when they do (a common one: re-run 04-Priorities when scope grows, then 06-Stories). The kit shows you what's already there and asks what you want to change. It never overwrites a file silently: the old version is saved first in `_history/`, with the date and time in its name.

---

## If something goes wrong

- **"It said it saved a file, but I can't find it."** Each step saves inside its own folder. If a save fails, the assistant should say so and show you the content to save by hand. If it didn't, tell it: "Read the file back and show me."
- **The assistant isn't following the steps.** Say: "Open the workflow file for this step and follow it exactly."
- **It's asking for something you already gave it.** Say: "Check the earlier step's file first."

---

Copyright 2025-26 Judith Sol Group, LLC
