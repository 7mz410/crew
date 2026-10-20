# crew

A Claude Code skill for getting more done with cheaper models. One manager session (Opus at low effort) plans and reviews; Haiku agents do the reading, editing and test runs. The skill teaches both sides how to work so the cheap model gets it right the first time.

## Why it works

Most of the cost of agent work is not the first attempt. It is the retries: an agent that searched the wrong place, touched files it shouldn't have, or reported success on code that doesn't run. `crew` is built around removing those retries.

- **Briefs that Haiku can't misread.** Every agent gets the same template: one-sentence goal, the context the manager already found, exact files, scope fences, a "done when" command, and a capped report. No judgment calls are left to the cheap model.
- **The manager reviews the diff, not the report.** Agent reports can be wrong. The manager reads `git diff`, runs the check itself, sends one precise correction, and takes the task over if it fails twice.
- **Spawn only when it pays.** Small known edits are done directly; spawning an agent for a 5-line change costs more than the change.
- **Laziest code that works.** A seven-rung ladder (does it need to exist, does it already exist, stdlib, native platform, installed dependency, one line, minimum code) keeps diffs small, and small diffs are where bugs don't hide. Bug fixes go to the root cause, once.
- **Terse by default.** Replies drop filler and keep every fact, in the user's own language and dialect. It switches to full prose for security warnings and irreversible actions.
- **UI quality built in.** Design tokens, light and dark themes, WCAG contrast, keyboard and focus, every component state, mobile at 360 px, and first-class RTL support for Arabic, Hebrew, Persian and Urdu.
- **Safe by habit.** Look before deleting, never touch build outputs without asking, no secrets in files, no push or deploy without review and approval, and honest reporting of what was and wasn't verified.
- **Self-contained.** Every rule is in one file. Optional skills (`code-review`, `security-review`, `simplify`, and UI skills if installed) are used when present and never required.

## Install

```sh
git clone https://github.com/7mz410/crew.git
cp -r crew/crew ~/.claude/skills/
```

Then start a session with `/crew`. For the intended setup, run the main session on Opus with low effort; the skill sends agents to Haiku.

## Controls

- `stop voice`, `stop build`, `stop design`, `stop crew`: turn off one part.
- `normal mode`: turn everything off.
- `/crew voice lite|full|ultra`, `/crew build lite|full|ultra`: change intensity.

Your project's own `CLAUDE.md`, `PROJECT.md` or `README.md` always wins where it conflicts with the skill.

## License

MIT
