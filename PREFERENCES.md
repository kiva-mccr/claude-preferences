# Kiva's preferences for Claude

Last updated: 2026-11-26 - scanned: p2p-script-studio, Word-Tierlister, Diamagnetic-Gyro-Handheld,
Electrostatic-Motor-Controller-UI, FSO-PCB, Automated-Lens-Parameter-System, Linear-Circuits-2-Calculator,
FreeSpaceQR, Optical-Mounts, kivamccrxyz, Toggle-PC

How to read this: each bullet is a preference seen in Kiva's repos, with the repos it came from in brackets.
A project's own CLAUDE.md wins over this file where they differ.

## Pinned (hand-written)

<!-- Kiva's own section. The weekly update never edits, reorders or removes anything here. -->

## General workflow

- Go step by step through a roadmap file (ROADMAP.md) with stable step IDs; tick `[x]` as steps land, and never
  build a step Kiva has not approved. [p2p-script-studio, Word-Tierlister]
- Show mock-ups (or screenshots) of any design or visible fix and agree the look and open choices before building
  it fully. [p2p-script-studio, Word-Tierlister]
- One thread per feature: finish, test and merge each feature before starting the next, so nothing is left half
  built if a session runs out. [p2p-script-studio, Word-Tierlister]
- Ask before changing a decision already settled; keep settled, shelved and archived decisions in the roadmap's
  "Decisions" section. [p2p-script-studio, Word-Tierlister]
- Finish a step with: tests passing, roadmap ticked, README (and developer docs) updated in the same commit, and a
  short summary that says plainly what was verified and what was only simulated or never seen for real.
  [p2p-script-studio, Word-Tierlister]
- Keep a `.claude/CHECKLIST.md` per project and run through it before handing a round over. [p2p-script-studio,
  Word-Tierlister]
- Every prompt, before finishing: tidy what was touched (dead code, stale comments and names, debug lines, unused
  imports, scratch files out of the repo). [p2p-script-studio, Word-Tierlister]
- Last thing on every prompt: update the project's CLAUDE.md if something important changed (Next, a rule learnt,
  Known gaps, commands), keep it short, and push it with the rest. Finished steps go in the roadmap, not in
  CLAUDE.md. [p2p-script-studio, Word-Tierlister]
- Keep a "Known gaps (never seen for real)" list in CLAUDE.md for behaviour that was only faked or simulated, so Kiva
  can confirm it on real hardware or real machines. [p2p-script-studio, Word-Tierlister]
- Save tokens: search large files (the roadmap) by step ID instead of reading them whole; read a file's note before
  the file; for a text-only change run only the tests that cover it. [p2p-script-studio, Word-Tierlister]
- Write in plain language, short sentences, for a non-specialist; user-facing errors are plain-language messages,
  never raw tracebacks. [p2p-script-studio, Word-Tierlister]

## Design and UI

- Minimalist above all ("minimalist as hell"): few controls, no sidebars or nested menus, no badges, streaks or
  goals. [p2p-script-studio, Word-Tierlister]
- No native browser dialogs (alert, confirm, validation bubbles) and no OS-native popups that grab input; show
  messages and checks in the page or in the app's own styled dialogs. [p2p-script-studio, Word-Tierlister]
- Help text that explains how a feature works should be hideable (p2p: `class="help"`). [p2p-script-studio]
- Light look by default with an optional dark mode; soft pastel colours with good contrast (about 7:1 text);
  short, tasteful animations that never block input. [Word-Tierlister]
- Check UI at a small laptop screen and a large monitor; take screenshots of every changed screen plus odd states
  (empty, long text, error). [p2p-script-studio, Word-Tierlister]
- Keys and labels come from one place (a key map), never hard-coded in hints, buttons or menus. [Word-Tierlister]

## Code style

- Every code file gets a short note beside it (`name.md`): purpose, then "Rules and pitfalls"; read it before
  editing and add the rule or bug there when fixing one. [p2p-script-studio, Word-Tierlister]
- Keep files small: a new screen, panel or chunk of logic gets its own file rather than growing a big one.
  [p2p-script-studio, Word-Tierlister]
- No copy-paste: a third copy of the same few lines becomes a helper. [p2p-script-studio, Word-Tierlister]
- Enforce layering (a file imports only from earlier layers) where a project defines it. [Word-Tierlister]
- Measure speed on realistic big data before and after performance work; keep per-action work fast.
  [p2p-script-studio, Word-Tierlister]
- JS/TS formatting (Prettier): print width 100, single quotes, 4-space indent for code and SCSS.
  [kivamccrxyz]

## Languages and frameworks

- Web apps: Svelte 5 + TypeScript + Vite, static hosting (GitHub Pages), no server, database or sign-in. Earlier
  site: React + TypeScript + Vite + SCSS modules. [p2p-script-studio, kivamccrxyz]
- Desktop apps: Python with tkinter, SQLite for saves, PyInstaller builds released through GitHub Releases.
  [Word-Tierlister]
- Microcontrollers: Arduino `.ino` sketches (ESP32 displays with LVGL for UIs). [Diamagnetic-Gyro-Handheld,
  Electrostatic-Motor-Controller-UI, Toggle-PC, FreeSpaceQR]
- Quick maths and lab tools: Jupyter / Google Colab notebooks; MATLAB for lab capture; LaTeX for generated
  datasheets. [Linear-Circuits-2-Calculator, Automated-Lens-Parameter-System, FreeSpaceQR]
- Prefer free, local, private tools: no paid services; models run in the browser rather than on a server.
  [p2p-script-studio]

## Testing

- Every new behaviour or widget gets a test. [p2p-script-studio, Word-Tierlister]
- Never hand over a red test; if a test had to change, say why. Fix flaky tests at the race, never add retries.
  [p2p-script-studio, Word-Tierlister]
- Tests never go online; fake external services, hardware and other computers, and record that they were faked.
  [p2p-script-studio, Word-Tierlister]
- Web: Vitest for units, Playwright for end-to-end, `svelte-check` for types. Python: self-test scripts run by one
  shell runner, plus pyflakes and vulture. [p2p-script-studio, Word-Tierlister]

## Git and PRs

- Claude works on `claude/...` branches and opens a PR; main is protected (merge only through a PR, required test
  check). [p2p-script-studio, Word-Tierlister]
- Claude may merge its own PRs once checks pass: turn on auto-merge right after opening, then check the deploy and
  live site. [p2p-script-studio]
- Commit messages: a short plain sentence, often led by the step ID ("AP-67: ..."). [p2p-script-studio,
  Word-Tierlister]
- CI skips pushes that change only `.md` files or docs; PRs always run tests. [p2p-script-studio, Word-Tierlister]
- Pin GitHub Actions to commit hashes and audit dependencies. [p2p-script-studio]
- Never commit secrets or private content; public repos hold only code and made-up examples. [p2p-script-studio,
  Word-Tierlister]

## Docs

- README.md is the user-facing introduction in plain words (screenshots for new screens); a separate developer guide
  (DEVELOPERS.md) where the project is big enough. Update them in the same commit as the change.
  [p2p-script-studio, Word-Tierlister]
- Kiva corrects typos and wording in READMEs and UI text by hand: proofread user-facing text. [p2p-script-studio,
  Word-Tierlister]
- Licences: MIT or GPL-3.0 for software, Creative Commons for hardware, optics and notebooks (Kiva changed
  p2p-script-studio from GPL-3.0 to MIT). [all]

## Hardware, firmware and PCB projects

- PCBs in KiCad: keep schematics, boards, Gerbers (zipped too), BOM CSV, STEP models and PDF schematics together in
  the repo. [FSO-PCB, Diamagnetic-Gyro-Handheld]
- Keep 3D model paths relative so the project opens on another machine; add thermal relief on through-hole pads.
  [Diamagnetic-Gyro-Handheld]
- Delete KiCad lock files (`~*.lck`) rather than committing them. [Diamagnetic-Gyro-Handheld]
- Iterate boards as numbered versions (fso-pcb-1, -2, -3). [FSO-PCB]
- Optics: Zemax files and parametric mount designs live beside the code. [FreeSpaceQR, Optical-Mounts]

## Per-project notes

- p2p-script-studio: scripts never go in the repo; files in `.studio/` are written once and never edited; the
  security rules (CSP, untrusted script files) are in its CLAUDE.md.
- Word-Tierlister: `tierlist.py` stays at the top; build the release zip with `tools/check_release.py`, never by
  hand; the repo must stay public.

## Changed this week

- First run: the document was created from all eleven repos.

## Open questions

- Spelling: Word-Tierlister's docs use British spelling ("colour", "Licence"), but Kiva changed "Licence" to
  "License" in its README. Which should Claude use in new text?
- Generated files: Automated-Lens-Parameter-System and the KiCad repos commit build output (LaTeX .aux/.log,
  .ipynb_checkpoints, KiCad backup zips). Should Claude add .gitignore entries for these, or keep them?
- Hardware repos have no CLAUDE.md, tests or checklist. Should the software workflow (roadmap, mock-ups first,
  notes beside files) apply to them too?
