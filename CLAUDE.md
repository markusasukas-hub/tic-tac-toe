# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the game

Open `tictactoe.html` directly in any browser — no build step or server required:

```bash
open tictactoe.html
```

## Git workflow

**Commit and push after every piece of completed work** — no exceptions. This keeps GitHub in sync at all times so no progress is ever lost and any state can be reverted.

Rules:
- Commit after each logical unit of work (a feature added, a bug fixed, a file created/deleted).
- Never batch multiple unrelated changes into one commit.
- Write commit messages in the imperative, present tense: `"Add AI opponent"` not `"Added AI opponent"` or `"Adding AI opponent"`. Keep the subject line under 72 characters.
- Always push immediately after committing — local-only commits defeat the purpose.

```bash
git add <changed files>
git commit -m "Short imperative summary of what changed"
git push
```

Remote: `https://github.com/markusasukas-hub/tic-tac-toe` on branch `main`.

## Architecture

The entire project is a single file (`tictactoe.html`) with three inline sections:

- **CSS** (`<style>`) — dark theme using a fixed color palette: `#1a1a2e` background, `#e94560` for X / `#a8dadc` for O. All visual states (hover, taken, win) are handled via CSS classes toggled by JS.
- **HTML** — static board of 9 `.cell` divs addressed by `data-i` (0–8), plus a scoreboard and restart button.
- **JavaScript** (`<script>`) — no framework, no modules. State lives in three variables: `board` (9-element array), `current` (active player), `over` (game ended flag). `WINS` is a constant array of the 8 winning index triples used by `checkWin()`. Scores persist across restarts in the `scores` object but reset on page reload.
