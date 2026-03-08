# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**VECTORION** is a browser-based entity simulation game. The entire project lives in a single file: `simulation.html`. There is no build system, no package manager, and no test suite — just open the file in a browser.

## Running the Project

Open `simulation.html` directly in a browser. No server required.

## Architecture

Everything — HTML structure, CSS styles, and JavaScript logic — is inlined in `simulation.html`.

**Simulation grid**: 100×100 tile grid rendered on an HTML5 `<canvas>` element. Each tile is a `CELL`-sized pixel square, dynamically sized to fit the window.

**Entity structure**: Each entity is a polyomino (a multi-cell irregular shape) with:
- `x, y` — top-left grid position
- `cells` — array of `{dx, dy}` offsets forming the shape
- `movementProperty` — one of: `destroy`, `bounce`, `stop`, `devour`, `change`
- `dir` — current movement direction `{dx, dy}`
- `speed` — tiles moved per tick
- `stopped`, `trail`, `speedTrail`, `changeTarget`, `def` (visual metadata)

**Movement properties / collision rules**:
- `destroy` — eliminates anything it touches; two destroyers annihilate each other
- `bounce` — deflects off walls and other entities
- `stop` — freezes on collision; a second hit unfreezes it
- `devour` — absorbs entities it touches, growing larger; destroyed by `destroy`
- `change` — acts as its `changeTarget` property on collision, then mutates to a new random property

**Tick loop (`step()`)**: Two-phase per tick:
1. Compute final positions by sub-stepping each entity `speed` tiles, bouncing off walls
2. Detect collisions along full paths using `pathsOverlap()`, then apply destroy/devour/stop/bounce/change resolution

**UI layout**:
- Fixed top bar (game name, autosave toast, version label)
- Left column: canvas inside `.game-area` (resizable via drag handle)
- Right column: entity legend list + entity editor panel
- Fixed bottom bar: tick/collision stats, keyboard controls
- Overlay modal system: Main Menu → New Game config → active simulation; ESC/game-name click opens Game Options during play

**Save / Load**:
- Autosave to `localStorage` key `vectorion_autosave` on pause
- Export/Import as `.json` files via `importEntities()` / export button

**Key bindings (during simulation)**:
- `Space` — start / pause
- `Enter` — single step (when paused)
- `ESC` or `O` — open Game Options overlay
- `+` / `-` — increase / decrease speed
- Clicking game name in header — open Game Options

## Key Constants and Globals

| Symbol | Description |
|---|---|
| `COLS`, `ROWS` | 100 × 100 grid dimensions |
| `TRAIL_LENGTH` | 14 — length of movement trail |
| `ROLE_COLORS` | Color/glow definitions keyed by movement property |
| `currentVersion` | Version string displayed in UI (currently `"v6.00"`) |
| `speed` | Tick interval in ms (default 80, range 20–500) |
| `diagonalMode` | Allows 8-directional movement when true |
| `showSpeedTrail` | Renders ghost cells at intermediate positions for fast entities |

## Planned Work (todo.md)

Active work-in-progress features and future plans are tracked in `todo.md`. Check it before starting new features to avoid duplication.
