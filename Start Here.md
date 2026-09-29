# Start Here — Team Setup

A short interview so every later step knows what you're building with, what your course requires, and when it's due. Takes about 5 minutes. Writes `Team.md`.

## Opener
Cover, in a few short lines and your own words:
- **What:** a few quick questions about your project setup before we start.
- **Why:** every later step uses these answers, so the suggestions fit your stack, your course's rules and your deadline, and you don't have to repeat yourself.
- **What I'll ask:** your project's name, tech stack, whether people log in, outside services, anything your course requires, your deadline, where you track work, and anything you're bringing from the workshop. One at a time; type **skip** on any of them.
- **What you'll get:** a short `Team.md` file the rest of the kit reads.
- **Next:** 01-Idea (or 02-Pitch if you already have an idea).

## What good looks like
- [ ] `Team.md` exists at the top of the kit folder and was read back after saving.
- [ ] It has the project or team name. It does **not** ask for member names or roles (assigning work is the team's job, not the kit's).
- [ ] The tech stack is filled in, even if some parts say "not decided", along with whether the app has user accounts and any outside services it uses.
- [ ] Anything the course requires (login, a number of APIs, a framework) is recorded, or it says `none` or `not sure`.
- [ ] The deadline or demo date is a real date (or what the team said, or `(skipped)`).
- [ ] The board choice is one of: GitHub, Trello, both, none (with the repo name if GitHub, when they know it).
- [ ] Anything brought in from the workshop (sketches, board photos) is saved in the kit's `workshop/` folder and listed, or the list says `none`.
- [ ] Nothing was guessed: every blank the student skipped says `(skipped)` (the workshop list says `none`).

## IN
- Nothing required. This is the first step.
- If `Team.md` already exists, see **Re-running this step**.

## Process
Give the opener (standing rule 1). Then ask these one at a time. Wait for each answer. If an answer already covers a later question, confirm it in one line instead of asking.

1. **Project or team name.** "What's your project or team called? A working name is fine."
2. **Tech stack.** Ask as one question with four parts: "What's your tech stack? Frontend, backend, database, and hosting. 'Not decided' is a fine answer for any of them." Why it matters: "so later suggestions use tools you'll actually use." Record their words; don't explain their own terms back to them.
3. **Accounts.** "Will people log in to your app with their own account?" Why it matters: "apps with accounts build log-in first, so it changes the order of everything." Yes, no or not decided are all fine.
4. **Outside services.** "Will it use any outside services, like a maps, weather or payments API?" (An **API** here means another company's service your app asks for data.) Why it matters: "outside services take extra setup, so I'll plan time for them."
5. **Course requirements.** "Does your course require anything specific for this project, like user login, a certain number of APIs, or a particular framework?" Why it matters: "so we don't plan a version your instructors won't accept." `Not sure` is fine: record it and suggest they check with their instructors. If they name a number of APIs, ask once: "Does your course mean outside services (another company's API), or does your own backend's API count?" If this clashes with their answer to question 4 (say, "no outside services" but "at least 2 APIs"), point it out in one line.
6. **Deadline or demo date.** "When is your demo or deadline?" Why it matters: "it decides how much fits in your first version." Record it as a date. If they give a week or a length ("2 weeks"), ask once for the actual date; if they don't know, record what they said.
7. **Board.** "Where will you track your work: GitHub (Issues or Projects), Trello, both, or none?" Why it matters: "at step 06 I'll give you your user stories in a form you can load into that board. You can change this later." Then, whatever the board: "Where does your code live? A GitHub repo name (like `your-team/your-app`), or skip if you don't have one yet." Why it matters: "at step 06 I can copy your stories straight into it." Only if the board is GitHub or both **and** they gave a repo, ask as its own question: "Do you use a GitHub Project board? If so, what's its number, and who owns it (your organisation or someone's GitHub username)? The number is at the end of its web address, like …/projects/3." If they didn't give a repo, write `none` and say they can add a Project board at step 06.
8. **Workshop materials.** "Do you have anything from the workshop to bring in? For example a photo of your sticky-note board, a sketch, or a tldraw export." Why it matters: "so the kit builds on what you already did instead of starting over." If yes, ask them to put the files in a folder called `workshop` inside this kit, and list them. You can read images. If they can only paste an image into the chat, describe what's on it in `Team.md` and note "share it again at step 04", because a pasted image isn't saved. If they say no, skip, or "nothing ready yet", write `none`.

[CHECKPOINT] "Here's what I'll save, so the later steps can use it. Does this look right?" Show the draft `Team.md` in chat. Change anything they correct.

Then write the file (standing rules 7 and 8).

## OUT
`Team.md` at the top of the kit folder:

```
# Team — [project or team name]

_Last updated: YYYY-MM-DD_

## Tech stack
- Frontend: ...
- Backend: ...
- Database: ...
- Hosting: ...
- User accounts: [yes / no / not decided]
- Outside services: [e.g. Open-Meteo weather API, or none]

## Course requirements
[e.g. user login and at least 2 APIs / none / not sure — check with instructors]

## Deadline
[date or what the team said]

## Board
[GitHub / Trello / both / none]
Code repo: [your-team/your-app, or (skipped)]
GitHub Project: [number and owner, e.g. 3 (your-team); none; or not using GitHub]

## Stories copied to
not yet

## Brought in from the workshop
- [workshop/file name, or "none"] — [what it is]
```

Every line comes from the student, so this file doesn't need `(team decision)` labels. Anything they skipped says `(skipped)`.

## Re-running this step
If `Team.md` exists, show what's in it and ask: "Want to change anything here?" Snapshot the old file to `_history/Start Here/Team-YYYY-MM-DD-HHMM.md` before editing. Only ask about the parts they want to change; don't redo the whole interview. If they change course requirements, accounts or stack, name the later files that may now be out of date (standing rule 12). If they add or change the board or repo, say that step 06 can now copy the stories and that `create-issues.sh` will be regenerated.

## Finish
Say:
- "I saved `Team.md` and read it back to check it."
- "Open it and check it looks right."
- "Next: **01-Idea**, to find a project idea together. If your team already has an idea, skip to **02-Pitch**."
