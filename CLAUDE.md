# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file browser game — `tictactoe.html` contains all HTML, CSS, and JavaScript inline. No build step, no dependencies, no package manager.

## Running the Project

Open `tictactoe.html` directly in a browser. No server required.

## Architecture

All logic lives in one file:

- **State**: `board` (9-element array), `current` (active player), `over` (game-ended flag), `scores` (persists across restarts)
- **Win detection**: `checkWin()` iterates the 8 hardcoded `WINS` combos against the board array
- **Rendering**: DOM is updated directly — no framework, no virtual DOM
- **Restart**: `init()` resets board/current/over and clears cell classes, but scores are intentionally preserved

## Git & GitHub

- Remote: `https://github.com/saurabhkumar81/Test1`
- After every meaningful change, commit with a clean descriptive message and push to `origin master` immediately — do not batch unrelated changes into one commit and do not leave the session with unpushed work
- Commit messages should describe the *why* or *what changed*, not just "update file"
