# Start Here — Team Setup

A short interview so every later step knows who you are, what you're building with, and when it's due. Takes about 5 minutes. Writes `Team.md`.

## What good looks like
- [ ] `Team.md` exists at the top of the kit folder and was read back after saving.
- [ ] It names the team, every member with a role, and **one** person who runs the kit.
- [ ] The tech stack is filled in, even if some parts say "not decided", along with whether the app has user accounts and any outside services it uses.
- [ ] The deadline or demo date is a real date (or marked `(skipped)`).
- [ ] The board choice is one of: GitHub, Trello, both, none (with the repo name if GitHub, when they know it).
- [ ] Anything brought in from the workshop (sketches, board photos) is saved in the kit's `workshop/` folder and listed, or the list says `none`.
- [ ] Nothing was guessed: every blank the student skipped says `(skipped)` (the workshop list says `none`).

## IN
- Nothing required. This is the first step.
- If `Team.md` already exists, see **Re-running this step**.

## Process
Ask these one at a time. Wait for each answer. The student can type **skip** on any of them.

Open with: "Hi! Before we start on your project, I'll ask a few quick questions about your team. One at a time, and you can type **skip** on any of them. First: what's your team or project called?"

1. **Team or project name.**
2. **Team members and roles.** "Who's on the team, and what's each person's role? Roles can be loose, like 'frontend', 'backend', 'design', or 'a bit of everything'."
3. **Who is running the kit.** "Which one of you is running this kit? One person runs it and shares the files with everyone else, so the team has one version of the truth." If they name two people, explain that once and ask them to pick one.
4. **Tech stack.** Ask as one question with four parts: "What's your tech stack? Frontend, backend, database, and hosting. 'Not decided' is a fine answer for any of them." If they use a term you think a teammate might not know, don't explain it back to them; just record it.
5. **Accounts.** "Will people log in to your app with their own account?" Yes, no or not decided are all fine. If they already said this while answering the stack question, confirm it in one line instead of asking again. Then, as its own question: "Will it use any outside services, like a maps, weather or payments API?" (An **API** here means another company's service your app asks for data.)
6. **Deadline or demo date.** "When is your demo or deadline?" Record it as a date. If they give a week ("week 12"), ask once for the actual date; if they don't know, record what they said.
7. **Board.** "Where will you track your work: GitHub (Issues or Projects), Trello, both, or none?" Explain in one line why it matters: "At step 06 I'll give you your user stories in a form you can load into that board." If they said GitHub or both, ask one follow-up: "What's your project repo called on GitHub (like `your-team/your-app`)? Skip if you don't have one yet." Then, as its own question: "Do you use a GitHub Project board? If so, what's its number? It's at the end of its web address, like …/projects/3."
8. **Workshop materials.** "Do you have anything from the workshop to bring in? For example a photo of your sticky-note board, a sketch, or a tldraw export." If yes, ask them to put the files in a folder called `workshop` inside this kit, and list them. You can read images. If they can only paste an image into the chat, describe what's on it in `Team.md` and note "share it again at step 04", because a pasted image isn't saved. If they say no or skip, write `none`.

[CHECKPOINT] Show the student the draft `Team.md` in chat and ask: "Does this look right?" Change anything they correct.

Then write the file (following standing rules 2 and 3).

## OUT
`Team.md` at the top of the kit folder:

```
# Team — [team or project name]

_Last updated: YYYY-MM-DD_

## People
| Name | Role |
|---|---|
| ... | ... |

**Kit runner:** [name] (runs the kit and shares the files with the team)

## Tech stack
- Frontend: ...
- Backend: ...
- Database: ...
- Hosting: ...
- User accounts: [yes / no / not decided]
- Outside services: [e.g. Open-Meteo weather API, or none]

## Deadline
[date or what the team said]

## Board
[GitHub / Trello / both / none]
GitHub repo: [your-team/your-app, (skipped), or not using GitHub]
GitHub Project: [number and owner, e.g. 3 (your-team), or none]

## Stories copied to
[added by step 06 if the team copies stories into their project repo]

## Brought in from the workshop
- [workshop/file name, or "none"] — [what it is]
```

Every line comes from the student, so this file doesn't need `(team decision)` labels. Anything they skipped says `(skipped)`.

## Re-running this step
If `Team.md` exists, show what's in it and ask: "Want to change anything here?" Snapshot the old file to `_history/Start Here/Team-YYYY-MM-DD-HHMM.md` before editing. Only ask about the parts they want to change; don't redo the whole interview.

## Finish
Say:
- "I saved `Team.md` and read it back to check it."
- "Open it and check it looks right."
- "Next: **01-Idea**, to find a project idea together. If your team already has an idea, skip to **02-Pitch**."
