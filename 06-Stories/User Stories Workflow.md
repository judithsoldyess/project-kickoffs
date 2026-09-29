# User Stories Workflow

Turns the team's broken-down features into user stories, in the format taught in the workshop, ordered so the team can build top to bottom. Writes `06-Stories/user-stories.md`, plus a board export for GitHub or Trello.

A **user story** is a precise, testable description of one thing a user can do. Not a vague feature request. You teach while you write: every ordering decision gets a short "why".

## Opener
Cover, in a few short lines and your own words:
- **What:** we'll turn your tasks from step 05 into user stories. A story is one thing a person can see or do, written so anyone on the team can build and test it.
- **Why:** stories are what go on your board. Each one is small enough to finish in about a day, and the numbering is your build order, so the team always knows what's next.
- **How your tasks fit:** up to 3 tasks from `Breakdown.md` become one story. I'll show you which tasks went where, and each story's tasks go on its board card as a checklist.
- **What I'll ask:** first, whether my plan (which tasks go into which story) looks right. Then I'll show you the first story or two, one at a time, so you can see the format; after that I can write the rest.
- **What you'll get:** `user-stories.md`, plus your GitHub or Trello export.
- **Next:** 07-Prototype turns the stories into a clickable prototype.

## What good looks like
- [ ] Every story uses the workshop format: `Story N — As a [user type], I can …` (usually "a user") with **Goal / Design / Technical Considerations / Acceptance Criteria**.
- [ ] Every story has 2–5 Given/When/Then blocks, covering the happy path and at least one failure, validation or empty state.
- [ ] The one thing that is **new** in each story's Technical Considerations is in bold (or the story says it reuses an earlier one).
- [ ] Dependencies are written as `depends on: Story X` (or `Story X, Story Y`), and the numbering is the build order: auth first when there are accounts; the first screen first when there aren't. Project setup is either folded into Story 1 (one task) or listed as a Setup checklist before Story 1 (more than one). Stories added later say where they fit (`build after: Story X`).
- [ ] Every story is tagged `[Must]`, `[Should]` or `[Could]` and says which feature(s) it covers. Won'ts only appear if the team asked.
- [ ] Every feature the team chose is covered: by its own stories, or inside another story (listed in the Coverage table).
- [ ] Tech-stack items show up inside Technical Considerations or the Setup checklist, never as their own story, and match the stack in `Team.md`.
- [ ] **No story covers more than 3 tasks from `Breakdown.md`** (about a day of work). The AI split any bigger story before showing it and said why.
- [ ] The read-back showed a feature → tasks → stories table, and the counts (features, tasks, stories).
- [ ] Each story's issue or card ends with its tasks as a checklist.
- [ ] Review checklist (**INVEST**, used to check stories, not as the story format): each story is **I**ndependent enough to build once its dependencies are done, **N**egotiable in how it's built, **V**aluable to a real user, **E**stimable, **S**mall (about a day, at most 3 tasks), and **T**estable through its acceptance criteria.
- [ ] The board export (if any) matches `user-stories.md` story for story, and nothing was run for the student.

## IN
- `05-Breakdown/Breakdown.md` — the tasks to turn into stories (including any **Setup** section).
- `04-Priorities/MoSCoW.md` — tiers and tech-stack items.
- `Team.md` — stack and accounts (for ordering and Technical Considerations), board, code repo and GitHub Project (for the export).
- `02-Pitch/Pitch.md` — context (optional).
- Any workshop sketches listed in `Team.md` (optional): use them so each story's **Design** matches what the team already drew.
- If `Breakdown.md` is missing but `MoSCoW.md` exists, you can work straight from the features; say so. If `Breakdown.md` only covers some features (say, Musts and Shoulds), write the others straight from their line in `MoSCoW.md` and say so in the read-back. If both files are missing: "Stories are built from your priorities (**04-Priorities**) and breakdown (**05-Breakdown**). Want to run those, or paste your Must list or a photo of your board?" You can read images.
- If `06-Stories/user-stories.md` already exists, see **Re-running this step** before writing anything.

## Worked example — what a finished story looks like

Every story you write must match this structure exactly.

---

## Story 5 — As a user, I can see restaurants serving specific cuisines `[Must]`

_Covers: Cuisine filter_

**Goal**
The user wants to browse restaurants near them, filtered to only the type of food they're in the mood for.

**Design**
A row of filter chips appears above the restaurant list, one chip per cuisine type (Italian, Indian, Mexican). Tapping a chip highlights it and immediately filters the list below. The list stays sorted closest-first. A visible "no results" message appears when no restaurants match. Tapping the chip again deselects it and restores the full list.

**Technical Considerations**
- Same card list component as the base restaurant list; no new card UI needed.
- List remains sorted by distance to the user's selected location.
- **The filter runs against the already-fetched list: a filter in the browser, not a new request to the server.**
- Deselecting the chip restores the full list without a page reload.

*depends on: Story 3 (can't filter a list that doesn't exist yet)*

**Acceptance Criteria**

Given I have a list of restaurants on the screen
When I tap the "Indian" chip
Then I only see restaurants that serve Indian food, still sorted closest-first

Given I have a cuisine filter selected
When I tap the chip again to deselect it
Then I see the full restaurant list again

Given no nearby restaurants serve the selected cuisine
When I apply the filter
Then I see a message that says "No restaurants match — try a different cuisine" instead of a blank screen

---

Four sections. One screen, one interaction, one outcome.

## Edge cases: same story or their own story?

Edge cases (empty states, validation failures, errors) are required, not afterthoughts. They are where most of the real engineering work lives. The rule for where each one goes:

- **A message or small change inside a screen that otherwise works → stays in that story's Acceptance Criteria.** The "No restaurants match" message above appears on the working list screen after the same action (tapping a chip), so it's one more Given/When/Then block in Story 5. Validation messages on a form work the same way.
- **A different screen, or its own logic → its own story.** If the edge case sends the user to a different screen, or needs its own engineering (saving something, a retry that has to keep and resend what the user did, a rule that changes what other people see), it gets a story. A "Try again" button that just repeats the same request stays in the Acceptance Criteria.
- **Fits both?** Give it its own story only when it's its own feature in `MoSCoW.md` or has a task in `Breakdown.md` that is only about it. If it shares a task with the main behaviour, keep it in the Acceptance Criteria. A retry only needs its own story when something has to be stored so it can be sent later (a queued message), not when the user's input is still on screen.

Example that stays in the story (validation on the same form):

> Given I'm on the sign-up form
> When I submit it with the email field empty
> Then I stay on the form and see "Please enter your email" under the email field

Example that becomes its own story (a different screen the user lands on):

> ## Story 11 — As a user, I can see a clear page when a shared trip link no longer works `[Should]`
> _Covers: Share a trip link_
> **Goal:** someone who opens an old or deleted trip link understands what happened instead of seeing an error or a blank page.
> **Design:** a "This trip isn't available" page with a short explanation and a "Go to my trips" button. …
> *depends on: Story 9*

In the prototype (step 07), a screen's empty and error *states* are shown with a toggle whether or not they have their own story. This rule is only about how the work is split into stories.

## Tech-stack items are not user stories

Cards like "REST API", "Firebase", "Gemini integration" or "Postgres" name a technology, not something a user does. You can't finish "As a user, I can ___" with them.

- If `MoSCoW.md` already lists them under tech-stack items, use them as inputs to Technical Considerations.
- If you spot a new one, flag it: "'[card]' is a technical component, not something a user does, so it isn't its own story. It'll appear in the Technical Considerations of the first story that uses it." Ask the student to confirm.
- Use the stack in `Team.md` for all Technical Considerations. If the stack says "not decided", keep them general and say so once.

## Process

### Step 1 — Read and read back
Give the opener (standing rule 1). Read the IN files. Read back, grouped by tier, what you'll turn into stories:
- Musts (and their breakdown tasks)
- Shoulds
- Coulds
- Won'ts: "I see these are out of scope for now; I'll leave them out unless you ask."
- Features with no breakdown (you'll write them from the feature line).
- Tech-stack items and how you'll treat them.
- **Setup** tasks from `Breakdown.md` and where they'll go (see Step 2).

**Plan the stories and show the work** (standing rules 4 and 6). Group each feature's tasks into stories of **at most 3 tasks** (about a day of work). A feature with 5 tasks becomes 2 stories, not 1. Split along what the user sees (the happy path first, then errors or extras). Then show the plan as a small table, one row per story, with the counts above it. Name each story by what the person can see or do (not the technical work), and give each task range a few words so the student can tell what it is:

> 5 features → 17 tasks → 8 stories
>
> | Feature | Tasks (from Breakdown.md) | Story |
> |---|---|---|
> | Photo diagnosis | 1–2 (photo form, send it off) | Story 1: take and send a photo |
> | Photo diagnosis | 3–4 (show the result) | Story 2: see the diagnosis |
> | Photo diagnosis | 5 (failure message) | Story 3: when the diagnosis fails |

Features that are "Built into" others show up as Acceptance Criteria in those stories; say which.

[CHECKPOINT] "This is how your tasks become stories on your board. Each story is one thing a person can see or do, about a day of work. Does anything here surprise you, or is something you'd expect missing? 'Looks good' and 'not sure, keep going' are fine answers." Wait for an answer. Then ask one more question, with its why: "Does your app have more than one kind of user, like a regular user and an admin? It decides how each story starts."  Use their words for user types ("As an organizer, I can …"); otherwise "As a user".

### Step 2 — Work out the build order
Before writing any story, decide the order. Explain the key decisions to the student in a sentence each.

- **With accounts: auth goes first, always.** Also say what a logged-out person sees first (the Log in page, or a Welcome page with its own story). Create account and log in / log out are Stories 1 and 2. Why: every feature that needs to know who the user is depends on auth. You can't save a favourite without a logged-in user to save it to. (**Auth** is short for authentication: proving who you are, usually by logging in.) If signing up also logs the user in, put the session setup in Story 1, and say where Story 1's success lands before later screens exist (a simple placeholder page).
- **Without accounts: the first screen goes first.** Story 1 is the first screen a user sees (usually the main list, with its empty state).
- **Setup tasks** from `Breakdown.md` aren't user stories (no user does them), but they have to happen first. If there's **one** Setup task, fold it into Story 1's Technical Considerations. If there's **more than one**, don't: Story 1 would get too big. List them in a `## Before Story 1: Setup` checklist at the top of `user-stories.md`, and they become one "Setup" issue or card on the board. Say which you did in the read-back.
- **Dependency chains decide the order.** If a story needs another story done first, the other one gets the lower number. Write `depends on: Story X` (or `Story X, Story Y`) in every story that has one. This chain is the team's build order: they code top to bottom.
- **Showing a list and submitting a form are separate stories.**
- **One screen, one state change, one story.** Two features on the same screen that need different engineering work are two stories. A message-only edge case is not "different engineering"; it stays in the Acceptance Criteria (see the edge-case rule above).

### Step 3 — Write in batches, one tier at a time
There's no limit on how many stories you write, but write them in batches so the team can review:

1. **Must stories.** Before showing any story, check it yourself (standing rules 4 and 15): the heading says "As a [user type], I can …", no more than 3 tasks, a failure, validation or empty-state block, a bold item that really is new. If a story is too big, split it and say so: "I split this into two stories because it was about [N] days of work."
   - First, show a short legend, one line each: **Goal** = why the person wants it; **Design** = what they see and tap; **Technical Considerations** = notes for whoever builds it, with the new thing in bold; **Acceptance Criteria** = Given/When/Then checks that say when it's done.
   - [CHECKPOINT] Show Story 1 on its own: "This is the first thing your team builds. Does it sound right? Say yes, or tell me what you'd change." Then the same for Story 2.
   - Then offer: "Want me to write the rest of the Musts, or keep going one at a time?" Either is fine. If they ask you to finish, label those stories honestly (standing rule 9).
   - Save (Step 4).
   - When the 3-task limit (Step 1) would leave a story with little value on its own (just "set up the diagnosis service"), move that "set up and prove it works" task to the Setup checklist instead, and tell the student you moved it and why. If a story is the first half of a feature, say what the team can show when it's done ("the photo reaches the service and comes back").
2. Ask: "Want to continue with your **Should** stories: all [N], or pick which ones? They'll be added to the same file, continuing the numbering." Only continue if they say yes. Same self-check, review and save.
3. Same for **Could**.
4. Only write Won't stories if the team asks.

If a batch will be very large (say more than 15 stories), mention it once: "This will be about [N] stories, a lot to review in one go. Want me to do them in two halves?" It's their call.

Every story follows this exact structure. Don't skip or add sections.

- **Heading:** `## Story [N] — As a [user type], I can [do the thing] `[Must/Should/Could]``. Always "I can", even for error and empty-state stories: "I can see a clear message when my photo can't be read", not "I get a message…" or "I'm told…". The story is about what the person can do or see.
- **Covers line:** `_Covers: [feature name(s) from MoSCoW.md]_`
- **Goal** — one plain sentence from the user's point of view. What do they want, and why does it matter to them? No technical language.
- **Design** — what the screen looks like and what the user taps, types or swipes. Be concrete: name the fields, what happens on submit, what feedback they see. If there are two meaningful states (heart outline vs. heart filled), describe both.
- **Technical Considerations** — 3–5 bullets for the developer. **The one consideration that is new in this story (something the team hasn't handled in an earlier story) is in bold.** If several things are new, bold the biggest one and name the rest plainly. Reused patterns aren't bolded again. If nothing is new, write a last bullet: "No new technique: reuses the pattern from Story X." This shows where the engineering effort lives. A tech-stack item gets bold only when it's the biggest new thing in that story.
- **Dependency line** (if any), in italics after the Technical Considerations: *depends on: Story X* or *depends on: Story X, Story Y*.
- **Acceptance Criteria** — Given/When/Then blocks. Minimum 2, maximum 5. Cover the happy path and at least one failure, validation or empty-state path. For settings and preference stories, that can be "saving fails" or "what the user sees before they've set anything". More than 5 means it's a specification, not a story: split it.

### Step 4 — Save `user-stories.md`
Follow standing rules 7 and 8. Save after each batch so nothing is lost. After every save, re-check dependencies across the **whole** file: a new Should story might depend on a Must story, and that needs to be written in. No acceptance criterion may need a story with a higher number (Story 2 can't send the user to a screen from Story 6). If a check changes a story the team already approved, say what changed and why, and ask once. Update the Coverage table at the top so every chosen feature points to the stories that cover it.

### Step 5 — Board export
Check the board in `Team.md`. If it's missing, ask: "Where will you track your work: GitHub, Trello, both, or none?"

**Card files, for every board (including none).** Write one file per story in `06-Stories/issues/story-NN.md`, plus `issues/setup.md` if there's a Setup checklist. Each file is what goes on that story's card or issue: the story text from its heading up to the next story's heading, **without** the `---` separator line at the end (never split the file on `---` lines, which a student might use inside a story), then the story's tasks as a checklist:

  ```
  **Tasks**
  - [ ] Photo upload form that accepts a phone photo (Breakdown: Photo diagnosis 1)
  - [ ] Send the photo to the diagnosis service and get an answer (Breakdown: Photo diagnosis 2)
  ```

  Tasks come from `Breakdown.md`. For a story whose feature has no breakdown, write its tasks yourself (at most 3), label each `(suggested — not from Breakdown.md)`, show them in the Step 1 plan, and offer to add them to `Breakdown.md`. If the feature was marked `(team said: not sure, keep going)` in 05, carry that label onto its stories. `setup.md` holds the Setup checklist in the same `- [ ]` form.

**GitHub** → also write `06-Stories/create-issues.sh` and `issues/list.txt`, with one line per issue in order: `tier|title|body file`, for example `Must|Story 1 — As a user, I can create an account|issues/story-01.md` (the Setup issue first, titled `Setup — before Story 1`, label `Must`). If a title contains `|`, replace it with `/` in that file. **Never put story titles inside the script itself**: titles are the team's own text, and characters like `$`, `"` or a backtick would break the script or run something unintended. The script only reads `list.txt` as plain text. Fill in `REPO` from `Team.md`'s code repo, and `PROJECT_NUMBER` and `PROJECT_OWNER` from its GitHub Project line. If the Project number or owner is missing (and it doesn't say `none`), ask once for only what's missing, and add the answer to `Team.md` (standing rule 12). GitHub shows the **Tasks** lines as a task list with tick boxes. The script must:
- Start with a comment explaining what it does and how to run it.
- Check that the `gh` command (GitHub's command-line tool) is installed and logged in, and stop with a clear message if not.
- Work out which repo it will use, **without changing folder first**, check it exists, and stop with a clear message if it can't.
- Read the list from `issues/list.txt` as plain text, and check every body file exists before creating anything.
- Print the list of issues it will create (title and label) and the repo, then ask `Create these N issues? (y/n)` and stop on anything other than `y`.
- Skip any story that already has an issue, matching on the `Story N` start of the title (so running it twice, or after a title change, doesn't make duplicates). The Setup issue matches only its whole title, so a team's own "Setup ESLint" issue doesn't count.
- Create the labels `Must`, `Should`, `Could` if they don't exist.
- If a GitHub Project number is set, check the login has the `project` permission before starting, and add each issue to the Project.

Use this template:

```bash
#!/usr/bin/env bash
# Creates one GitHub issue per user story, labelled Must / Should / Could.
# Run it from a terminal opened in your project repo folder:
#   bash "path/to/Project Kickoff/06-Stories/create-issues.sh"
# Needs the GitHub CLI (https://cli.github.com), logged in with: gh auth login
# It shows you the list and asks before creating anything.
set -euo pipefail
DIR="$(cd "$(dirname "$0")" && pwd)"   # where this script and issues/ live

REPO=""           # e.g. "your-team/your-app". Empty = the repo of the folder you run it from.
PROJECT_NUMBER="" # GitHub Project number, or leave empty
PROJECT_OWNER=""  # the Project's owner (user or org), if using a Project

command -v gh >/dev/null || { echo "The GitHub CLI (gh) isn't installed. See https://cli.github.com"; exit 1; }
gh auth status >/dev/null 2>&1 || { echo "Log in first: gh auth login"; exit 1; }
if [ -z "$REPO" ]; then
  REPO=$(gh repo view --json nameWithOwner -q .nameWithOwner 2>/dev/null) || {
    echo "Couldn't tell which repo to use. Run this from your project repo folder, or set REPO at the top."; exit 1; }
fi
gh repo view "$REPO" >/dev/null 2>&1 || {
  echo "Can't find $REPO on GitHub. Check the name at the top of this script, and that you can see the repo."; exit 1; }
if [ -n "$PROJECT_NUMBER" ] && ! gh auth status 2>&1 | grep -q "'project'"; then
  echo "Adding to a Project needs one more permission. Run: gh auth refresh -s project"; exit 1
fi

# The list of issues lives in issues/list.txt, one per line: tier|title|body file
# It's read as plain text, never run as code, so any characters in a title are safe.
STORIES=()
while IFS= read -r line || [ -n "$line" ]; do
  [ -n "$line" ] && STORIES+=("$line")
done < "$DIR/issues/list.txt"

for s in "${STORIES[@]}"; do
  IFS='|' read -r _ _ body <<<"$s"
  [ -f "$DIR/$body" ] || { echo "Missing file: $DIR/$body. Nothing was created."; exit 1; }
done

EXISTING=$(gh issue list --repo "$REPO" --state all --limit 5000 --json title -q '.[].title') || {
  echo "Couldn't read the existing issues from $REPO (network or GitHub problem). Nothing was created. Try again in a minute."; exit 1; }
EXISTING_LC=$(printf '%s\n' "$EXISTING" | tr '[:upper:]' '[:lower:]')
echo "Repo: $REPO"
TODO=()
for s in "${STORIES[@]}"; do
  IFS='|' read -r tier title _ <<<"$s"
  key=$(printf '%s' "${title%% — *}" | tr '[:upper:]' '[:lower:]')   # "story 7" or "setup"
  whole=$(printf '%s' "$title" | tr '[:upper:]' '[:lower:]'); whole="${whole// — / - }"; whole="${whole// – / - }"
  found=""
  while IFS= read -r t; do
    if [[ "$key" == story\ * ]]; then
      # matches "Story 7 — …", "Story 7 - …", "story 7: …" but not "Story 70"
      if [[ "$t" == "$key" || ( "$t" == "$key"* && ! "${t:${#key}:1}" =~ [0-9] ) ]]; then found=1; break; fi
    else
      # anything else (the Setup issue) must match its whole title ("Setup - before Story 1" counts)
      t2="${t// — / - }"; t2="${t2// – / - }"
      if [[ "$t2" == "$whole" ]]; then found=1; break; fi
    fi
  done <<<"$EXISTING_LC"
  if [ -n "$found" ]; then echo "  (already on GitHub, skipping) $title"
  else echo "  [$tier] $title"; TODO+=("$s"); fi
done
[ ${#TODO[@]} -gt 0 ] || { echo "Nothing new to create."; exit 0; }
read -r -p "Create these ${#TODO[@]} issues? (y/n) " ok
[ "$ok" = "y" ] || { echo "Stopped. Nothing was created."; exit 0; }

for l in Must Should Could; do gh label create "$l" --repo "$REPO" --force >/dev/null; done
for s in "${TODO[@]}"; do
  IFS='|' read -r tier title body <<<"$s"
  url=$(gh issue create --repo "$REPO" --title "$title" --body-file "$DIR/$body" --label "$tier")
  echo "Created: $url"
  if [ -n "$PROJECT_NUMBER" ]; then
    gh project item-add "$PROJECT_NUMBER" --owner "$PROJECT_OWNER" --url "$url" >/dev/null
  fi
done
echo "Done."
```

**Never run this script for the student.** Tell them (and add: "If you rename an issue on GitHub, keep the 'Story N' at the start so the script can recognise it"): "To create the issues, open a terminal in your project repo folder and run `bash \"<path to kit>/06-Stories/create-issues.sh\"`. It shows you the list and asks before creating anything." On Windows, they can run it in Git Bash or WSL, or create issues by hand from the `issues/` files. Mention once: GitHub gives issues its own numbers (#1, #2…), which won't match story numbers. The issue titles keep "Story N", so `depends on: Story X` still makes sense on the board.

**Trello** → Trello has no built-in CSV import, so don't make a CSV. Write `06-Stories/trello-cards.txt`: one story title per line, in story order, with the tier at the front (`[Must] Story 1 — As a user, I can create an account`). If there's a Setup checklist, the first line is `[Must] Setup — before Story 1`, and the student pastes the checklist into that card (or adds it as a Trello checklist). Tell the student: "In Trello, click **Add a card** on a list, paste all the lines at once, and Trello offers to create one card per line. Choose that. Then open each card and paste the story from its file in `06-Stories/issues/` into the description, and add the lines under **Tasks** as a Trello checklist (open the card, choose **Checklist**, and paste them; Trello makes one item per line). You can also create Must / Should / Could labels in Trello and add them as you go." Mention once that CSV import Power-Ups exist (Blue Cat, Excelefy, EasyCSV) if they want to try one, but the plain paste works without any add-on.

**Both** → write both. **None** → skip the export.

### Step 6 — Copy into the project repo
If `Team.md` shows no project repo yet, skip this step and say: "Your files stay here in the kit for now. When you have a project repo, run 06 again and choose to copy them." Otherwise:

[CHECKPOINT] "Your team will build from the copy in your project repo, so it's handy to have it there. Want me to copy `user-stories.md` (and the export) into your project repo now?"
- If yes, ask for the path to their project folder, then ask where in it: the top level, or a `docs/` folder (suggest `docs/`). Copy only after they answer.
- For **every** file you'd copy: if a file with that name is already there, don't overwrite it. Ask whether to replace it, save alongside it with the date (`user-stories-YYYY-MM-DD.md`, adding `-2` if that's taken too), or skip it.
- Before replacing a file the kit didn't write, copy it into the kit at `_history/06-Stories/repo-<name>-YYYY-MM-DD-HHMM.<ext>` and say where, so nothing is lost.
- After copying, read the copied files back and confirm. Then, in `Team.md`, replace `not yet` under **Stories copied to** with `<path> (YYYY-MM-DD)`, so later runs know where the copies are.
- **Re-copying later:** if the files there are the kit's own earlier copies (check `Team.md`), ask once: "Replace your earlier copies with the updated ones?" Use the per-file question only for files the kit didn't put there. Never save `create-issues.sh` or `issues/` alongside old ones (two scripts would create duplicates): replace or skip.
- If no, tell them where the files are so they can copy them later.

## OUT
`06-Stories/user-stories.md`:

```
# User Stories — [product name]

_Last updated: YYYY-MM-DD_
_Build order is top to bottom. Tiers: [Must] → [Should] → [Could]._
_All stories below were reviewed by the team (team decision) unless marked (suggested — not yet agreed)._
_[N] features → [N] tasks → [N] stories (tasks from `05-Breakdown/Breakdown.md`)._

## Before Story 1: Setup
_(Only if there's more than one Setup task.)_
- [ ] [Create the project and deploy a blank page]
- [ ] [...]

## Coverage
| Feature (from MoSCoW.md) | Tier | Stories |
|---|---|---|
| Create an account | Must | 1 |
| Friendly error messages | Must | inside 2, 4, 7 (Acceptance Criteria) |

---

## Story 1 — As a user, I can [...] `[Must]`

_Covers: [feature]_

**Goal**
...

**Design**
...

**Technical Considerations**
- ...
- **...**
- ...

*depends on: Story X*

**Acceptance Criteria**

Given ...
When ...
Then ...

Given ...
When ...
Then ...

---

## Story 2 — ...
```

Plus, for every board: `06-Stories/issues/story-NN.md` (and `issues/setup.md`), each ending with its **Tasks** checklist. Depending on the board: `06-Stories/create-issues.sh` and `issues/list.txt`, and/or `06-Stories/trello-cards.txt`.

## Re-running this step
If `user-stories.md` exists, show a short summary first: how many stories per tier and the highest story number. Then ask: "Do you want to **add** new stories, **update** specific stories, or **start over**?" Before changing anything, snapshot `user-stories.md` **and every export file** (`create-issues.sh`, `issues/`, `trello-cards.txt`) to `_history/06-Stories/`.
- **Add:** continue numbering from Story [N+1]; never renumber existing stories. If a new story is for a kind of user you haven't used yet ("a friend with the link"), confirm the words with the team. If a new story belongs earlier in the build order than its number suggests (a new Must after the Coulds, say), add a line under its heading: `_build after: Story X_`.
- **Update:** ask which story numbers; change only those. To change a story's tier, update its tag and tell the student to change the label on the board too. If the change adds or removes tasks, update that story's task checklist and the count line at the top, and offer to update `Breakdown.md` (standing rule 12).
- **Start over:** before rebuilding, compare the current stories with `Breakdown.md`. For anything that only exists in the stories (added in an earlier update), ask whether to keep it, and suggest re-running 05 to add it there. Then rebuild. If Story 1 in an older file still carries several Setup tasks, offer to move them into the Setup checklist (story numbers don't change).

Every time, re-check dependencies across the whole file and update the Coverage table. Then ask: "Have you already created the GitHub issues or Trello cards?"
- **No:** regenerate the export files in full.
- Either way, always regenerate `create-issues.sh` from the current template (it's safe to re-run: it skips stories that already have an issue).
- **Yes:** keep the export files complete (so they always match `user-stories.md`), and tell the student exactly what to do on the board: new stories → run `create-issues.sh` again (it skips stories that already have an issue), or paste only the new lines into Trello; changed stories → edit the existing issue or card by hand, because re-creating them would make duplicates. For each changed story, name the issue or card and say whether to change its title, its description, its task checklist, or several of these. Stories no longer in the file → name each issue or card and ask whether to close/archive it or keep it for later. Never delete anything for them.

If `Team.md` shows you copied files into the team's project repo before (Step 6), offer to copy them again, with the same don't-overwrite rules. Finally, tell the student which files are now out of date (`07-Prototype/screens.md`, `prototype.html`, and `05-Breakdown/Breakdown.md` if a feature's tier changed or it has no breakdown yet) (standing rule 12).

## Finish
- "I saved `06-Stories/user-stories.md` and read it back." Plus any export files.
- "Open `user-stories.md` and read Story 1 together as a team. Is it clear enough that someone could start building it today?"
- "Story 1 gets built first; each story depends only on stories above it."
- "Next: **07-Prototype**, to see your stories as a clickable prototype."
