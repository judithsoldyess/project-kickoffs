# User Stories Workflow

Turns the team's broken-down features into user stories, in the format taught in the workshop, ordered so the team can build top to bottom. Writes `06-Stories/user-stories.md`, plus a board export for GitHub or Trello.

A **user story** is a precise, testable description of one thing a user can do. Not a vague feature request. You teach while you write: every ordering decision gets a short "why".

## What good looks like
- [ ] Every story uses the workshop format: `Story N — As a [user type], I can …` (usually "a user") with **Goal / Design / Technical Considerations / Acceptance Criteria**.
- [ ] Every story has 2–5 Given/When/Then blocks, covering the happy path and at least one failure, validation or empty state.
- [ ] The one thing that is **new** in each story's Technical Considerations is in bold (or the story says it reuses an earlier one).
- [ ] Dependencies are written as `depends on: Story X` (or `Story X, Story Y`), and the numbering is the build order: auth first when there are accounts; the first screen first when there aren't. Project setup is either folded into Story 1 (one piece) or listed as a Setup checklist before Story 1 (more than one). Stories added later say where they fit (`build after: Story X`).
- [ ] Every story is tagged `[Must]`, `[Should]` or `[Could]` and says which feature(s) it covers. Won'ts only appear if the team asked.
- [ ] Every feature the team chose is covered: by its own stories, or inside another story (listed in the Coverage table).
- [ ] Tech-stack items show up inside Technical Considerations or the Setup checklist, never as their own story, and match the stack in `Team.md`.
- [ ] Review checklist (**INVEST**, used to check stories, not as the story format): each story is **I**ndependent enough to build once its dependencies are done, **N**egotiable in how it's built, **V**aluable to a real user, **E**stimable, **S**mall (a day or two of work at most), and **T**estable through its acceptance criteria.
- [ ] The board export (if any) matches `user-stories.md` story for story, and nothing was run for the student.

## IN
- `05-Breakdown/Breakdown.md` — the pieces to turn into stories (including any **Setup** section).
- `04-Priorities/MoSCoW.md` — tiers and tech-stack items.
- `Team.md` — stack and accounts (for ordering and Technical Considerations), board and GitHub repo (for the export).
- `02-Pitch/Pitch.md` — context (optional).
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
- **Fits both?** Give it its own story only when it's its own feature in `MoSCoW.md` or has a piece in `Breakdown.md` that is only about it. If it shares a piece with the main behaviour, keep it in the Acceptance Criteria. A retry only needs its own story when something has to be stored so it can be sent later (a queued message), not when the user's input is still on screen.

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
Read the IN files. Read back, grouped by tier, what you'll turn into stories:
- Musts (and their breakdown pieces)
- Shoulds
- Coulds
- Won'ts: "I see these are out of scope for now; I'll leave them out unless you ask."
- Features with no breakdown (you'll write them from the feature line).
- Tech-stack items and how you'll treat them.
- **Setup** pieces from `Breakdown.md` and where they'll go (see Step 2).

Show roughly which pieces will become which story. A story usually covers 1–4 pieces from one feature. Features that are "Built into" others will show up as Acceptance Criteria in those stories; say which.

[CHECKPOINT] "Does this look right?" Wait for confirmation. Then ask one more question: "Does your app have more than one kind of user, like a regular user and an admin?" Use their words for user types ("As an organizer, I can …"); otherwise "As a user".

### Step 2 — Work out the build order
Before writing any story, decide the order. Explain the key decisions to the student in a sentence each.

- **With accounts: auth goes first, always.** Create account and log in / log out are Stories 1 and 2. Why: every feature that needs to know who the user is depends on auth. You can't save a favourite without a logged-in user to save it to. (**Auth** is short for authentication: proving who you are, usually by logging in.) If signing up also logs the user in, put the session setup in Story 1, and say where Story 1's success lands before later screens exist (a simple placeholder page).
- **Without accounts: the first screen goes first.** Story 1 is the first screen a user sees (usually the main list, with its empty state).
- **Setup pieces** from `Breakdown.md` aren't user stories (no user does them), but they have to happen first. If there's **one** Setup piece, fold it into Story 1's Technical Considerations. If there's **more than one**, don't: Story 1 would get too big. List them in a `## Before Story 1: Setup` checklist at the top of `user-stories.md`, and they become one "Setup" issue or card on the board. Say which you did in the read-back.
- **Dependency chains decide the order.** If a story needs another story done first, the other one gets the lower number. Write `depends on: Story X` (or `Story X, Story Y`) in every story that has one. This chain is the team's build order: they code top to bottom.
- **Showing a list and submitting a form are separate stories.**
- **One screen, one state change, one story.** Two features on the same screen that need different engineering work are two stories. A message-only edge case is not "different engineering"; it stays in the Acceptance Criteria (see the edge-case rule above).

### Step 3 — Write in batches, one tier at a time
There's no limit on how many stories you write, but write them in batches so the team can review:

1. Write all the **Must** stories. Check every story against **What good looks like** yourself first (standing rule 8): especially that each one has a failure, validation or empty-state block, and that the bold item really is new. Fix what fails. [CHECKPOINT] Show them and ask: "Take a look at these Must stories. Anything to change before I save them?" Apply edits, then save (Step 4).
2. Ask: "Want to continue with your **Should** stories: all [N], or pick which ones? They'll be added to the same file, continuing the numbering." Only continue if they say yes. Same self-check, review and save.
3. Same for **Could**.
4. Only write Won't stories if the team asks.

If a batch will be very large (say more than 15 stories), mention it once: "This will be about [N] stories, a lot to review in one go. Want me to do them in two halves?" It's their call.

Every story follows this exact structure. Don't skip or add sections.

- **Heading:** `## Story [N] — As a [user type], I can [do the thing] `[Must/Should/Could]``
- **Covers line:** `_Covers: [feature name(s) from MoSCoW.md]_`
- **Goal** — one plain sentence from the user's point of view. What do they want, and why does it matter to them? No technical language.
- **Design** — what the screen looks like and what the user taps, types or swipes. Be concrete: name the fields, what happens on submit, what feedback they see. If there are two meaningful states (heart outline vs. heart filled), describe both.
- **Technical Considerations** — 3–5 bullets for the developer. **The one consideration that is new in this story (something the team hasn't handled in an earlier story) is in bold.** If several things are new, bold the biggest one and name the rest plainly. Reused patterns aren't bolded again. If nothing is new, write a last bullet: "No new technique: reuses the pattern from Story X." This shows where the engineering effort lives. A tech-stack item gets bold only when it's the biggest new thing in that story.
- **Dependency line** (if any), in italics after the Technical Considerations: *depends on: Story X* or *depends on: Story X, Story Y*.
- **Acceptance Criteria** — Given/When/Then blocks. Minimum 2, maximum 5. Cover the happy path and at least one failure, validation or empty-state path. For settings and preference stories, that can be "saving fails" or "what the user sees before they've set anything". More than 5 means it's a specification, not a story: split it.

### Step 4 — Save `user-stories.md`
Follow standing rules 2 and 3. Save after each batch so nothing is lost. After every save, re-check dependencies across the **whole** file: a new Should story might depend on a Must story, and that needs to be written in. Update the Coverage table at the top so every chosen feature points to the stories that cover it.

### Step 5 — Board export
Check the board in `Team.md`. If it's missing, ask: "Where will you track your work: GitHub, Trello, both, or none?"

**GitHub** → write `06-Stories/create-issues.sh` and one body file per story in `06-Stories/issues/story-NN.md` (the full story text), plus `issues/setup.md` if there's a Setup checklist (title `Setup — before Story 1`, label `Must`, listed first), and `issues/list.txt` with one line per issue in order: `tier|title|body file`, for example `Must|Story 1 — As a user, I can create an account|issues/story-01.md`. If a title contains `|`, replace it with `/` in that file. **Never put story titles inside the script itself**: titles are the team's own text, and characters like `$`, `"` or a backtick would break the script or run something unintended. The script only reads `list.txt` as plain text. Fill in `REPO`, `PROJECT_NUMBER` and `PROJECT_OWNER` from `Team.md`. If `Team.md` doesn't give a GitHub Project number and owner (or say `none`), ask once: "Do you use a GitHub Project board? If so, what's its number and who owns it?" Add the answer to `Team.md`'s `GitHub Project:` line (standing rule 9). The script must:
- Start with a comment explaining what it does and how to run it.
- Check that the `gh` command (GitHub's command-line tool) is installed and logged in, and stop with a clear message if not.
- Work out which repo it will use, **without changing folder first**, check it exists, and stop with a clear message if it can't.
- Read the list from `issues/list.txt` as plain text, and check every body file exists before creating anything.
- Print the list of issues it will create (title and label) and the repo, then ask `Create these N issues? (y/n)` and stop on anything other than `y`.
- Skip any story that already has an issue, matching on the `Story N —` start of the title (so running it twice, or after a title change, doesn't make duplicates).
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
  found=""
  while IFS= read -r t; do
    # matches "Story 7 — …", "Story 7 - …", "story 7: …" but not "Story 70"
    if [[ "$t" == "$key" || ( "$t" == "$key"* && ! "${t:${#key}:1}" =~ [0-9] ) ]]; then found=1; fi
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

**Trello** → Trello has no built-in CSV import, so don't make a CSV. Write `06-Stories/trello-cards.txt`: one story title per line, in story order, with the tier at the front (`[Must] Story 1 — As a user, I can create an account`). If there's a Setup checklist, the first line is `[Must] Setup — before Story 1`, and the student pastes the checklist into that card (or adds it as a Trello checklist). Tell the student: "In Trello, click **Add a card** on a list, paste all the lines at once, and Trello offers to create one card per line. Choose that. Then open each card and paste the full story from `user-stories.md` into its description. You can also create Must / Should / Could labels in Trello and add them as you go." Mention once that CSV import Power-Ups exist (Blue Cat, Excelefy, EasyCSV) if they want to try one, but the plain paste works without any add-on.

**Both** → write both. **None** → skip the export.

### Step 6 — Copy into the project repo
[CHECKPOINT] Ask: "Want me to copy `user-stories.md` (and the export) into your project repo now?"
- If yes, ask for the path to their project folder, then ask where in it: the top level, or a `docs/` folder (suggest `docs/`). Copy only after they answer.
- For **every** file you'd copy: if a file with that name is already there, don't overwrite it. Ask whether to replace it, save alongside it with the date (`user-stories-YYYY-MM-DD.md`, adding `-2` if that's taken too), or skip it.
- After copying, read the copied files back and confirm. Then add a line to `Team.md`: `Stories copied to: <path> (YYYY-MM-DD)`, so later runs know where the copies are.
- **Re-copying later:** if the files there are the kit's own earlier copies (check `Team.md`), ask once: "Replace your earlier copies with the updated ones?" Use the per-file question only for files the kit didn't put there. Never save `create-issues.sh` or `issues/` alongside old ones (two scripts would create duplicates): replace or skip.
- If no, tell them where the files are so they can copy them later.

## OUT
`06-Stories/user-stories.md`:

```
# User Stories — [product name]

_Last updated: YYYY-MM-DD_
_Build order is top to bottom. Tiers: [Must] → [Should] → [Could]._
_All stories below were reviewed by the team (team decision) unless marked (suggested — not yet agreed)._

## Before Story 1: Setup
_(Only if there's more than one Setup piece.)_
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

Plus, depending on the board: `06-Stories/create-issues.sh` and `06-Stories/issues/story-NN.md`, and/or `06-Stories/trello-cards.txt`.

## Re-running this step
If `user-stories.md` exists, show a short summary first: how many stories per tier and the highest story number. Then ask: "Do you want to **add** new stories, **update** specific stories, or **start over**?" Before changing anything, snapshot `user-stories.md` **and every export file** (`create-issues.sh`, `issues/`, `trello-cards.txt`) to `_history/06-Stories/`.
- **Add:** continue numbering from Story [N+1]; never renumber existing stories. If a new story belongs earlier in the build order than its number suggests (a new Must after the Coulds, say), add a line under its heading: `_build after: Story X_`.
- **Update:** ask which story numbers; change only those. To change a story's tier, update its tag and tell the student to change the label on the board too.
- **Start over:** before rebuilding, compare the current stories with `Breakdown.md`. For anything that only exists in the stories (added in an earlier update), ask whether to keep it, and suggest re-running 05 to add it there. Then rebuild. If Story 1 in an older file still carries several Setup pieces, offer to move them into the Setup checklist (story numbers don't change).

Every time, re-check dependencies across the whole file and update the Coverage table. Then ask: "Have you already created the GitHub issues or Trello cards?"
- **No:** regenerate the export files in full.
- Either way, always regenerate `create-issues.sh` from the current template (it's safe to re-run: it skips stories that already have an issue).
- **Yes:** keep the export files complete (so they always match `user-stories.md`), and tell the student exactly what to do on the board: new stories → run `create-issues.sh` again (it skips stories that already have an issue), or paste only the new lines into Trello; changed stories → edit the existing issue or card by hand, because re-creating them would make duplicates. For each changed story, name the issue or card and say whether to change its title, its description, or both. Stories no longer in the file → name each issue or card and ask whether to close/archive it or keep it for later. Never delete anything for them.

If `Team.md` shows you copied files into the team's project repo before (Step 6), offer to copy them again, with the same don't-overwrite rules. Finally, tell the student which later files are now out of date (`07-Prototype/screens.md`, `prototype.html`) if they exist (standing rule 10).

## Finish
- "I saved `06-Stories/user-stories.md` and read it back." Plus any export files.
- "Open `user-stories.md` and read Story 1 together as a team. Is it clear enough that someone could start building it today?"
- "Story 1 gets built first; each story depends only on stories above it."
- "Next: **07-Prototype**, to see your stories as a clickable prototype."
