# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Online multiplayer Tic Tac Toe — `tictactoe.html` is a single self-contained file with all HTML, CSS, and JavaScript inline. Uses **PeerJS** (loaded from unpkg CDN) for WebRTC peer-to-peer connections. No build step, no backend, no package manager.

## Running the Project

Open `tictactoe.html` directly in a browser. Both players need internet access for the initial WebRTC handshake via PeerJS's public signaling server; after that, traffic is direct between browsers.

## Architecture

All logic lives in one file with two screens:

- **Lobby**: Host clicks "Create Game" → gets a room code (their PeerJS peer ID); guest pastes the code and clicks "Join" to connect
- **Connection**: `setupConn()` wires up `conn.on('data')` for both sides; messages are `{ type: 'move', index }` or `{ type: 'restart' }`
- **State**: `board` (9-element array), `current` (active player), `over`, `scores` (persists across restarts), `myMark` / `opponentMark` (set at connect time — host = X, guest = O)
- **Turn enforcement**: `refreshStatus()` toggles the `disabled` class on cells so only the active player can click
- **Win detection**: `checkWin()` iterates 8 hardcoded `WINS` combos; `applyMove()` is called for both local and remote moves
- **Rendering**: DOM updated directly — no framework

## Git & GitHub

- Remote: `https://github.com/saurabhkumar81/Test1`
- After every meaningful change, commit with a clean descriptive message and push to `origin master` immediately — do not batch unrelated changes into one commit and do not leave the session with unpushed work
- Commit messages should describe the *why* or *what changed*, not just "update file"
