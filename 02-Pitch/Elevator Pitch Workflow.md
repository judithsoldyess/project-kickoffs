# Elevator Pitch Workflow

Turns the team's idea into a short, speakable elevator pitch: who it's for, what problem it solves, and why it's different. Writes `02-Pitch/Pitch.md`.

## Opener
Cover, in a few short lines and your own words:
- **What:** we'll turn your idea into a short pitch you could say out loud in 30 seconds.
- **Why:** a clear pitch keeps your whole team building the same thing, and it's what you'll say at your demo. It also shows early whether your idea is different enough from what people already use.
- **What I'll ask:** seven short things, one at a time: who it's for, their problem, the name (or I'll confirm the one from your idea), what kind of product it is, the main benefit, what people use today instead, and what makes yours different.
- **What you'll get:** `Pitch.md` with your pitch plus a one-liner and a README blurb.
- **Next:** 03-Features brainstorms everything the app could do.

## What good looks like
- [ ] Every template field is filled in by the team (or marked `(skipped)`).
- [ ] The customer is specific enough to picture one real person. Not "everyone", "users" or "people", but not narrowed further than the team wants either.
- [ ] There is a real alternative named (what people do today instead), even if it's "a spreadsheet" or "a group chat". If the alternative is genuinely good (a general AI assistant, a big app), the difference says why this beats it.
- [ ] The full pitch can be said out loud in 30 seconds: about 75 words, no more than 85 (count them).
- [ ] The team said it out loud and answered whether it sounds like a real person or a template.
- [ ] Three variants exist: 30-second spoken, one-liner (15 words or fewer), README blurb.
- [ ] Every version the team chose to keep is marked `(team decision)`; anything the AI reworded is marked `(suggested — not yet agreed)` until accepted.

## IN
- `01-Idea/Idea.md` if it exists. If it doesn't: "`Idea.md` comes from **01-Idea**. Want to run that, or just tell me your idea in a sentence?"
- `Team.md` for the team name (optional).
- If `02-Pitch/Pitch.md` already exists, see **Re-running this step**.

## Process
1. Give the opener (standing rule 1). If `Idea.md` exists, restate the idea in one line and ask if it's still right. If the student already told you the idea, restate it. Otherwise ask: "Describe your idea in one sentence." Wait for the answer before explaining the template.
2. Explain the template once:

   > **For** [target customer] **who** [need or problem], **[product name]** is a [category] **that** [key benefit]. **Unlike** [the alternative], **our product** [what's different].

3. Fill it in one field at a time, in this order. Ask one question per message, and offer a starting point from `Idea.md` when you have one (labelled as a suggestion):
   1. **Customer** — specific enough to picture one real person: "Who exactly? 'Busy people' is everyone. 'Parents of kids in after-school sports' is someone." If they push back on a narrower suggestion and their answer already names a real kind of person ("people who struggle to keep houseplants alive"), accept it.
   2. **Need** — the problem they have, in their words. (Why: the pitch only works if the problem feels real.)
   3. **Name** — the product name (a working name is fine). If they want ideas, offer 5–7 labelled suggestions and let them pick or change one.
   4. **Category** — app, tool, website, platform, etc. If they say a phone (native) app, ask what actually needs a phone (camera? notifications? offline?), and say plainly what building a native app costs against their deadline and stack. A mobile-friendly web app can often use the camera too. If they change the stack, offer to update `Team.md` (standing rule 12).
   5. **Benefit** — "Why would someone use this instead of just Googling it?"
   6. **Alternative** — what they do today instead. (Why: every product competes with something, even "doing nothing".)
   7. **Difference** — what makes yours better than that alternative. (Why: this is the line that makes someone try it.)
4. Write the full pitch from their answers. Count the words; if it's over about 85, tighten it.
5. **Stress-test it.** Check for and point out, one at a time, any of these:
   - Generic words ("easy", "seamless", "all-in-one") doing the work instead of a real benefit.
   - A customer that is still "everyone".
   - No real alternative, or an alternative nobody actually uses.
   - An alternative that's actually good (a general AI assistant, a big popular app). Then the difference has to say why someone would pick this instead.
   - A difference that's really just "it's an app".
   Suggest a fix for each (labelled as a suggestion). The team decides. If the difference promises something that may be hard to build (exact measurements, forecasts), note it under Parked for later as "check in 04/05" rather than arguing about it here.
6. Say: **"Now say it out loud. Does it sound like something a real person would say, or does it sound like a template?"** Wait for the answer. If it sounds like a template, help them reword it in their own voice.
7. Write three variants (all `(suggested — not yet agreed)` until they pick):
   - **30-second spoken** — the pitch as you'd say it, natural sentences, no brackets.
   - **One-liner** — 15 words or fewer.
   - **README blurb** — 2–3 sentences for the top of their project's README.
8. [CHECKPOINT] "These are the versions you'll use for your demo, your README and quick intros. Which do you want to keep?" "Keep them all" is a fine answer: mark every kept version `(team decision)`. Then, as its own question: "Do you want to change any words?"
9. Write `02-Pitch/Pitch.md` (standing rules 7 and 8). If the name or category changed something `Idea.md` recorded, offer to update it (standing rule 12).

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

## Parked for later
- [ideas for later versions, and promises to check in 04/05]

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
