# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the game

Open `tictactoe.html` directly in a browser — no build step, no server, no dependencies:

```bash
open tictactoe.html
```

## Architecture

The entire game is a single self-contained file (`tictactoe.html`) with inline CSS and JS — no frameworks, no bundler, no external assets.

**Game state** lives in four module-level variables:
- `board` — 9-element array of `'X'`, `'O'`, or `null`
- `current` — whose turn it is (`'X'` or `'O'`)
- `over` — boolean, true once the game ends
- `scores` — persists across restarts (`{ X, O, D }`)

**Display mapping** — `'X'`/`'O'` are the internal identifiers throughout; `EMOJI` and `NAME` maps translate them to the visible 👹/🧝 representations only at render time.

**Flow:** `handleClick` → mutates `board` → calls `render` → updates DOM. Win detection (`checkWin`) runs after every move against the hardcoded `WINS` array of winning index triplets.

## Claude Code settings

`.claude/settings.local.json` contains pre-approved permissions for Claude Code so common operations (opening the file in a browser, git commands, GitHub MCP calls) don't prompt for confirmation each time.

## Git

Remote is `git@github.com:farlol/tic-tac-toe.git`. SSH key in use: `~/.ssh/gatr_key`.
