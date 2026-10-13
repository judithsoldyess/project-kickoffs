# Changing the kit

This repo is the kit itself: Markdown workflow files plus one HTML template (`04-Priorities/sorter-template.html`). There is no build, lint or test tooling. These notes are for people editing the kit, not for teams using it.

- **`CLAUDE.md` and `AGENTS.md` hold the same rules.** They must stay identical apart from the one-line note at the top of `AGENTS.md`. Change one, change both.
- **Workflow files share a structure:** `Opener`, `What good looks like`, `IN`, `Process` (with `[CHECKPOINT]`s), `OUT`, `Re-running this step`, `Finish`. Keep that shape when adding or changing a step.
- **Files flow forward:** each step reads earlier steps' output files and writes its own into its folder (see rule 10 in `CLAUDE.md` for the chain). A change to one step's output format can break the steps that read it, so check the later workflows' `IN` sections.
- **Don't commit generated files.** `Team.md`, `Idea.md`, `_history/`, `workshop/` and the other step outputs are written in each team's own copy. In particular, `Start Here` treats an existing `Team.md` as a re-run, so a placeholder would make every team skip the interview.
- **`README.md` documents the steps table** for students; update it if a step's inputs or outputs change.
