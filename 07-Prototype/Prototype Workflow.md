# Prototype Workflow

Turns the user stories into a clickable prototype the team can open in any browser, plus a small style guide. Two passes: a quick text map of the screens first, then the polished prototype. Writes `07-Prototype/screens.md`, `07-Prototype/prototype.html` and `07-Prototype/style-guide.html`.

You already sketched screens by hand in the workshop. That was the thinking part. Here it's fine to make it look good.

A **prototype** is a fake version of the app that looks and clicks like the real thing but doesn't save real data. It's for checking the flow and the look before you build.

## What good looks like
- [ ] `screens.md` maps every screen to the stories it covers and the screens it links to, and the team confirmed it.
- [ ] `prototype.html` opens by double-clicking, with no install and no internet needed (one file; all styles and scripts inside it).
- [ ] Every screen in `screens.md` exists in the prototype and every navigation link between them works.
- [ ] Every screen can show its **empty, loading, error and success** states using a visible toggle, with states that make sense for that kind of screen (a state that truly can't happen says "Not applicable" and why).
- [ ] Real words from `Pitch.md` and the stories. No "lorem ipsum" placeholder text.
- [ ] Mobile-first layout that also works on a wide screen.
- [ ] Accessible by default: real headings, buttons and form labels; a visible focus outline when using the keyboard; text contrast of at least 4.5:1; colour is never the only way something is shown; images have alt text.
- [ ] `style-guide.html` shows the colours, type sizes, buttons, form fields, cards and state messages the prototype uses, with contrast ratios that were calculated, not guessed.
- [ ] It was clicked through at phone width (about 375 px): every screen, every state, no errors in the browser console.
- [ ] Layout or look suggestions from the AI are labelled as suggestions in `screens.md` until the team agrees.

## IN
- `06-Stories/user-stories.md` — the screens come from here. If missing: "The prototype is built from your stories (**06-Stories**). Want to run that, or paste the stories you want to prototype?"
- `02-Pitch/Pitch.md` — product name and real copy.
- `04-Priorities/MoSCoW.md` — tiers, so you can ask which to prototype.
- `Team.md` — stack (so the prototype's structure is easy to rebuild in their framework) and any workshop sketches listed there. If they have sketches, look at them: they're the team's first idea of the layout.
- If any output file already exists, see **Re-running this step**.

## Process

### Pass 1 — Quick flow check
1. Ask: "Which stories should the prototype show: Musts only, Musts and Shoulds, or everything?" (Suggest Musts and Shoulds.) Mark any screen that only exists for a Could story as `(Could)`.
2. Read the chosen stories. List every screen they need (a sign-up form, a list, a detail page, a settings page…). Stories that share a screen share a line.
3. For each screen, note: which stories it covers, how you get there, and where you can go from it.
4. Show a text map in chat, for example:

   ```
   Welcome ──► Sign up ──► Trips (empty) ──► New trip ──► Trip detail
      │                       ▲                              │
      └──► Log in ────────────┘◄─────────────────────────────┘
   ```

5. [CHECKPOINT] Ask: "Is this the flow your team pictures? Anything missing, extra, or in the wrong place?" Edit until they agree.
6. Save `07-Prototype/screens.md` with Look: "to be chosen" (standing rules 2 and 3). You'll fill in the Look after the next two questions; that's part of the same run, so no snapshot is needed.

### Pass 2 — Clickable prototype
7. Ask: "Pick a starting look, or give me your own colours and fonts:"
   - **Clean** — light background, neutral greys, one blue accent, lots of white space. Calm and professional.
   - **Bold** — dark text on white with a strong, saturated accent colour, heavy headings, high contrast. Confident and energetic.
   - **Warm** — soft off-white background, warm accent (terracotta or amber), rounded corners, friendly type. Approachable.

   Use the system font stack (`system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`) so nothing needs downloading, unless the team names a font.
8. You may recommend a layout (for example "bottom tab bar on mobile, because your three main screens are equal"), with a one-line reason. Label it as a suggestion and let the team decide. [CHECKPOINT] Then update the Look section of `screens.md`.
9. Build `prototype.html` to these rules:
   - **One file.** All CSS in a `<style>` tag, all JavaScript in a `<script>` tag. No frameworks, no build tools, no links to outside files. It must work offline by double-clicking.
   - **Screens** are `<section>` elements; only one is visible at a time. **Navigation uses the URL hash** (`#signup`, `#trips`) so the browser's back button works and each screen can be linked directly. Links between screens are real `<a href="#…">` links or `<button>`s. Use the bare screen name in the hash even when the real app would add an id (`#trip`, not `#trip?id=4`); note the real route in `screens.md`. After every screen change, scroll to the top. Don't give a section the same `id` as its hash (use `id="screen-trips"` for `#trips`), or the browser jumps down to it. A "skip to content" link should be a button that moves focus, so it doesn't fight the hash navigation.
   - **State toggle.** A small bar (clearly labelled "Prototype controls") with four buttons: Empty, Loading, Error, Success. Put it where it never covers the app's own navigation or header (check at phone width; if the app has a bottom tab bar, put the controls at the top, and leave space for them). Keep notes short (one line at phone width if you can); the bar gets taller when a note wraps, so keep the space in step with its real height. It changes what the current screen shows, and the chosen state stays selected when you move to another screen. The toggle announces its change to screen readers (`aria-live="polite"`). Write each state for that kind of screen:
     - **Lists and pages that load data:** Empty = nothing yet, with a helpful next step ("No trips yet" + a button); Loading = a skeleton or "Loading your trips…"; Error = "We couldn't load your trips. Try again." + a retry button; Success = realistic sample content.
     - **Forms:** Empty = the untouched form; Loading = submitting ("Saving…", button disabled); Error = validation messages next to the fields; Success = the confirmation. Submitting a form shows Loading briefly, then Success; submitting in Success goes to the next screen. If a form can't be used yet because there's nothing to choose from (no beds, no categories), show that as its Empty state instead, and say so in `screens.md`. A form that only loads data to fill a dropdown still follows these form rules.
     - **A page whose main job is showing loaded data and that also has a form** (a chat, a profile): use the page rules for Empty, Loading and Error, and show the form's own validation or send failure inside Error.
     - **No server** (data kept in the browser): Loading and Error stand for reading or saving that data (for example "Couldn't save — your browser storage is full").
     - **Static screens** (a welcome page): if a state truly can't happen, show a short "Not applicable: [reason]" note in the prototype controls instead of inventing one.
   - **Real content.** Product name, headings and copy from `Pitch.md` and the stories. Sample data that fits the product (real-looking names, dates and places).
   - **Mobile-first.** Design for a phone width first; use a media query to widen for larger screens. No sideways scrolling.
   - **Accessible defaults.** Semantic HTML (`header`, `nav`, `main`, `h1`–`h3` in order, `button` for actions, `a` for navigation); every form field has a `<label>`; a visible focus outline (`:focus-visible`); text contrast at least 4.5:1 against its background; errors shown with text and an icon or label, not colour alone; `alt` text on images (or `alt=""` for decoration); the page has a `lang` attribute and a `<title>`.
   - **Tech-stack friendly.** Keep each screen's markup self-contained so the team can lift it into their framework (a React component, a Django template…) later. Add a comment at the top of each screen: `<!-- Screen: Trips — Stories 5, 6, 8 -->`.
   - A short comment at the very top of the file: what it is, how to open it, and that it's a prototype with no real data.
10. Build `style-guide.html` the same way (one file, no outside links): colour swatches with their hex codes and the contrast ratio of text on each (calculate it with the WCAG formula: ratio = (L1 + 0.05) / (L2 + 0.05), where L is each colour's relative luminance; don't estimate); the type scale (h1, h2, h3, body, small); buttons (primary, secondary, disabled, focus); form fields (normal, focus, error with message); a card; and the four state messages (empty, loading, error, success).
11. Save both files (standing rules 2 and 3). Check that every screen from `screens.md` has a matching `<section>` and that every navigation link (`<a href="#…">`) points to a screen that exists. If you can open a browser, also open it at phone width (about 375 px; check `window.innerWidth` really says about 375, because some headless browsers won't go below 500 px, so use device emulation or a 375 px frame), click through every screen and every state, and check the console for errors; if you can't, ask the student to do this and tell you what they see. Fix anything that doesn't work.
12. Tell the student: "Double-click `07-Prototype/prototype.html` to open it in your browser. Click through it, and try the Prototype controls on each screen."

### Critique loop
13. Ask one question at a time, and wait for each answer. After each answer, revise before asking the next question:
    - "What's the first thing that feels wrong?"
    - "Is there a screen where you weren't sure what to click?"
    - "Does it look like your product, or like a template?"
14. Before each revision, snapshot every file you'll change to `_history/07-Prototype/` (for example `prototype-YYYY-MM-DD-HHMM.html`). If a change affects something that's also in `style-guide.html` (a colour, a button), update that too. Revise, save, read back, add a line to Critique notes in `screens.md`, and ask them to reload the page.
15. Stop when the team says it's good enough. It's a prototype; it doesn't need to be perfect.

## OUT
`07-Prototype/screens.md`:

```
# Screens — [product name]

_Last updated: YYYY-MM-DD_

## Flow
[text map]

## Screens
| Screen | Hash (real route) | Stories | Comes from | Goes to |
|---|---|---|---|---|
| Welcome | #welcome | 1, 2 | (start) | Sign up, Log in |
| Trip detail | #trip (/trips/:id) | 6, 7 | Trips | Edit trip |
| ... | | | | |

## Look
- Starting look: [Clean / Bold / Warm / team's own] (team decision)
- Layout: [...] (team decision) or (suggested — not yet agreed)
- Prototyped tiers: [Must / Must + Should / all]

## Critique notes
- Flow confirmed by the team: yes (Pass 1)
- [what the team said] → [what changed]
```

`07-Prototype/prototype.html` and `07-Prototype/style-guide.html` as described above.

## Re-running this step
If the files exist, ask: "Do you want to update the prototype for new or changed stories, change the look, or start over?" Snapshot every file you'll change to `_history/07-Prototype/` first. For new stories, add their screens to `screens.md` and the prototype without redesigning screens the team already approved.

## Finish
- "I saved `screens.md`, `prototype.html` and `style-guide.html`, and read them back."
- "Double-click `prototype.html` and click through it as a team."
- "That's the last step. Your `user-stories.md` is your build order; the prototype is your picture of where you're going. When scope changes, re-run **04-Priorities**, then **05-Breakdown**, **06-Stories** and this step for the features that changed."
