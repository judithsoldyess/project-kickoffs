# Elevator Pitch Workflow

Turns the team's idea into a short, speakable elevator pitch: who it's for, what problem it solves, and why it's different. Writes `02-Pitch/Pitch.md`.

## What good looks like
- [ ] Every template field is filled in by the team (or marked `(skipped)`).
- [ ] The customer is specific. Not "everyone", "users" or "people".
- [ ] There is a real alternative named (what people do today instead), even if it's "a spreadsheet" or "a group chat".
- [ ] The full pitch can be said out loud in 30 seconds: about 75 words, no more than 85 (count them).
- [ ] The team said it out loud and answered whether it sounds like a real person or a template.
- [ ] Three variants exist: 30-second spoken, one-liner (15 words or fewer), README blurb.
- [ ] The team's final choice is marked `(team decision)`; anything the AI reworded is marked `(suggested — not yet agreed)` until accepted.

## IN
- `01-Idea/Idea.md` if it exists. If it doesn't: "`Idea.md` comes from **01-Idea**. Want to run that, or just tell me your idea in a sentence?"
- `Team.md` for the team name (optional).
- If `02-Pitch/Pitch.md` already exists, see **Re-running this step**.

## Process
1. If `Idea.md` exists, restate the idea in one line and ask if it's still right. If the student already told you the idea, restate it. Otherwise ask: "Describe your idea in one sentence." Wait for the answer before explaining the template.
2. Explain the template once:

   > **For** [target customer] **who** [need or problem], **[product name]** is a [category] **that** [key benefit]. **Unlike** [the alternative], **our product** [what's different].

3. Fill it in one field at a time, in this order. Ask one question per message, and offer a starting point from `Idea.md` when you have one (labelled as a suggestion):
   1. **Customer** — push for specific: "Who exactly? 'Busy people' is everyone. 'Parents of kids in after-school sports' is someone."
   2. **Need** — the problem they have, in their words.
   3. **Name** — the product name (a working name is fine).
   4. **Category** — app, tool, website, platform, etc.
   5. **Benefit** — "Why would someone use this instead of just Googling it?"
   6. **Alternative** — what they do today instead.
   7. **Difference** — what makes yours better than that alternative.
4. Write the full pitch from their answers. Count the words; if it's over about 85, tighten it.
5. **Stress-test it.** Check for and point out, one at a time, any of these:
   - Generic words ("easy", "seamless", "all-in-one") doing the work instead of a real benefit.
   - A customer that is still "everyone".
   - No real alternative, or an alternative nobody actually uses.
   - A difference that's really just "it's an app".
   Suggest a fix for each (labelled as a suggestion). The team decides.
6. Say: **"Now say it out loud. Does it sound like something a real person would say, or does it sound like a template?"** Wait for the answer. If it sounds like a template, help them reword it in their own voice.
7. Write three variants (all `(suggested — not yet agreed)` until they pick):
   - **30-second spoken** — the pitch as you'd say it, natural sentences, no brackets.
   - **One-liner** — 15 words or fewer.
   - **README blurb** — 2–3 sentences for the top of their project's README.
8. [CHECKPOINT] Ask: "Which version of the full pitch is your team going with, and do you want to change any words?" Mark their choice `(team decision)`. Then ask, one at a time, whether they're happy with the one-liner and the README blurb, and mark each one they accept `(team decision)`.
9. Write `02-Pitch/Pitch.md` (standing rules 2 and 3).

## OUT
`02-Pitch/Pitch.md`:

```
# Pitch — [product name]

_Last updated: YYYY-MM-DD_
_Idea: [the team's one sentence]_

## Our pitch (team decision)
[the version the team chose, in their final words]

## Template
- Customer: ...
- Need: ...
- Name: ...
- Category: ...
- Benefit: ...
- Alternative: ...
- Difference: ...

## Variants
- 30-second spoken: ... (team decision) or (suggested — not yet agreed)
- One-liner: ...
- README blurb: ...

## Stress-test notes
- [what we checked and what changed]
- Said out loud: [real person or template? what we changed]

## Suggestions we turned down
- [...]
```

Include the `_Idea: …_` line only when there's no `01-Idea/Idea.md`.

## Re-running this step
If `Pitch.md` exists, show the team's current pitch and ask: "Do you want to sharpen this, start over, or just add variants?" Snapshot to `_history/02-Pitch/Pitch-YYYY-MM-DD-HHMM.md` first.
- **Sharpen:** only redo the fields they want to change.
- **Add variants:** add new variants as extra labelled lines under Variants. Don't touch "Our pitch" or "Template" unless they ask.
- **Start over:** run the whole process again.

## Finish
- "I saved `02-Pitch/Pitch.md` and read it back."
- "Open it and read the pitch out loud one more time."
- "Next: **03-Features**, to brainstorm everything your app could do."
