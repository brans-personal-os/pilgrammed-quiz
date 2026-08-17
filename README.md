# Calibration harness

What this is: a single self-contained page (`index.html`) that runs the sitting-1 protocol
(`plan/pressure-test.md`, battle-plan move 5) over the forty batch-A questions in `work/bank.md`.
No external scripts, styles, fonts or network calls — it works with the phone in airplane mode.

## Files

- `index.html` — the whole app: markup, styles and logic in one file, plus the forty questions
  copied character-for-character from `work/bank.md`.
- `icon-180.png` — 180x180 home-screen icon.
- `manifest.json` — web app manifest, referenced by `index.html`.
- `robots.txt` — disallows all crawlers.

## How it works

1. Start screen: an empty name box, a line stating whether the page is running in its own
   installed window or a browser tab, and a line reporting whether storage persistence was
   granted, denied, or is unsupported.
2. Typing a name and tapping Begin shows that name's unseen questions from the forty, one at a
   time, four options, shuffled fresh on every question, with no clock or progress indicator of
   any kind on screen.
3. Every answer is timed silently (milliseconds from the question becoming visible to the tap)
   and recorded with name, question id, provisional band, right/wrong and which mode produced it.
   Each answer is saved to the phone's local storage immediately, and the seen-list is kept per
   name (trimmed, case-insensitive) so a name is never shown a question it has already answered.
4. If a name has no unseen questions left, the page says so and returns to the start screen
   instead of repeating one.
5. When a name finishes its available questions, the page returns to the start screen so the
   next name can be entered. Nothing already recorded is cleared.
6. "View recorded results" shows every recorded answer, for every name, in a table and as
   plain tab-separated text in a copyable box with a Copy button.

## Publishing

This folder is meant to be published to the app's own public GitHub Pages repo
(`game-quiz-app-D-015`) and added to both boys' phone home screens from the real `github.io`
address. Brandon runs the publish personally. No child's name is written anywhere in this
folder — the name box is empty until someone types into it on the phone, and typed names live
only in that phone's local storage.
