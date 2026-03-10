# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**VECTORION** is a browser-based entity simulation game. The entire project lives in a single file: `simulation.html`. There is no build system, no package manager, and no test suite — just open the file in a browser.

## Running the Project

Open `simulation.html` directly in a browser. No server required.

## Architecture

Everything — HTML structure, CSS styles, and JavaScript logic — is inlined in `simulation.html`.

**Simulation grid**: Variable size tile grid rendered on an HTML5 `<canvas>` element. Dimensions set at game start via `MIN_COLS` / `MIN_ROWS` (default 100 × 100). Each tile is a `CELL`-sized pixel square, dynamically sized to fit the window.

**Entity structure**: Each entity is a polyomino (a multi-cell irregular shape) with:
- `x, y` — top-left grid position
- `cells` — array of `{dx, dy}` offsets forming the shape
- `movementProperty` — one of: `destroy`, `bounce`, `stop`, `devour`, `change`
- `dir` — current movement direction `{dx, dy}`
- `speed` — tiles moved per tick
- `stopped`, `trail`, `speedTrail`, `changeTarget`, `def` (visual metadata)
- `visualReaction` — `'ignore'` | `'follow'` | `'avoid'`; controls reaction to line-of-sight detections
- `seenEntity` / `followTarget` — current line-of-sight target and locked follow target
- `avoidTarget` / `avoidTypes` — active avoid target and array of movementProperty strings to avoid
- `customColor` — optional hex color override applied to the entity's visuals

**Movement properties / collision rules**:
- `destroy` — eliminates anything it touches; two destroyers annihilate each other
- `bounce` — deflects off walls and other entities
- `stop` — freezes on collision; a second hit resumes it in the direction of the incoming force
- `devour` — absorbs entities it touches, growing larger; destroyed by `destroy`
- `change` — acts as its `changeTarget` property on collision, then mutates to a new random property

**Visual reactions**:
- `ignore` — no reaction to line-of-sight
- `follow` — locks onto first seen entity and steers toward it
- `avoid` — steers away from seen entities whose `movementProperty` is in `avoidTypes`

**Tick loop (`step()`)**: Two-phase per tick:
1. Compute final positions by sub-stepping each entity `speed` tiles, bouncing off walls; apply follow/avoid steering
2. Detect collisions along full paths using `pathsOverlap()`, then apply destroy/devour/stop/bounce/change resolution; residual overlap guard prevents any remaining overlaps

**Entity Groups**:
- Entities can be shift-selected and grouped via the **CREATE GROUP** button
- Groups are displayed first in the entity list with a numbered/named header; ungrouped entities follow
- Each group auto-assigns a unique color (from `ENTITY_COLORS`) applied to all members on creation
- Groups are collapsible (▼/▶ chevron), editable (click header → bulk edit modal), and disbandable (with confirmation)
- Group state saved: `id`, `name`, `color`, `collapsed`, `memberIndices`

**UI layout**:
- Fixed top bar: game name (click to open options), autosave toast, stats (tick, collisions, status, speed), version label
- Middle row split into three horizontal sections:
  - **Left column** — canvas inside `.game-area`; width snaps to actual canvas size (no dead space)
  - **`.resize-handle`** — drag to resize left/right split
  - **Right column** (`.right-col`) — further split horizontally by `.resize-handle-v`:
    - **Entity list** (`.right-top-area`) — entity editor panel + multi-column entity legend with group sections; height matches play area
    - **Game log** (`.right-bottom-area`) — filterable event log (collision / vision / avoidance)
- Fixed bottom bar: two rows of keyboard shortcut groups, centered
- Overlay modal system: Main Menu → New Game config → active simulation; ESC/game-name click opens Game Options
- Shift key activates selection mode: cyan highlight + pulsing badge on entity list
- Bulk edit modal (cyan themed, `z-index 600`) — edit collision/vision reaction and color for multiple selected entities
- Group edit modal — same bulk edit modal with added group name field; opened by clicking group header
- Disband confirmation modal (red themed, `z-index 700`)

**Save / Load**:
- Autosave to `localStorage` key `vectorion_autosave` on pause
- Export/Import as `.json` files via `importEntities()` / export button
- Save payload (`buildSavePayload`) includes: `version`, `gameName`, `savedAt`, `tick`, `diagonalMode`, `showSpeedTrail`, `maxSpeed`, `simSpeed`, `cols`, `rows`, `log`, `entities`, `groups`
- Entity serialized via `serializeEntity()`: name, movementProperty, changeTarget, x, y, dir, stopped, cells, speed, visualReaction, avoidTypes, customColor
- Group serialized: id, name, color, collapsed, memberIndices

**Zoom**:
- `ZOOM_STEPS` array: `[0.25, 0.5, 0.75, 1.0, 1.5, 2.0, 3.0, 4.0]`
- Minimum zoom locked at 1.0 (no shrinking viewport)
- Mouse-wheel zoom centers on cursor position; `NUM0` resets to 100%
- `baseCELL` × zoom factor = `CELL`; pan clamped to grid bounds

**Key bindings (during simulation)**:
- `Space` — start / pause
- `Shift+Space` — single step (when paused)
- `ESC` or `O` — open Game Options overlay
- `Backspace` — start new simulation with defaults
- `NUM+` / `NUM-` — increase / decrease simulation speed
- `Shift+NUM+` / `Shift+NUM-` — zoom in / out
- `NUM0` — reset zoom
- Clicking game name in header — open Game Options

## Key Constants and Globals

| Symbol | Description |
|---|---|
| `COLS`, `ROWS` | Grid dimensions (dynamic; initialized from `MIN_COLS` / `MIN_ROWS`, default 100 × 100) |
| `MIN_COLS`, `MIN_ROWS` | Minimum grid size set at game start (default 100 × 100) |
| `TRAIL_LENGTH` | 14 — length of movement trail |
| `ROLE_COLORS` | Color/glow definitions keyed by movement property |
| `ENTITY_COLORS` | Array of 12 hex colors (+ null for default) used in color picker and auto-assigned to groups |
| `currentVersion` | Version string displayed in UI (currently `"v6.01"`) |
| `speed` | Tick interval in ms (default 120) |
| `diagonalMode` | Allows 8-directional movement when true (default `true`) |
| `showSpeedTrail` | Renders ghost cells at intermediate positions for fast entities |
| `maxEntityW`, `maxEntityH` | Max entity shape dimensions at spawn (default 4 × 4) |
| `maxSpeed` | Max entity speed at spawn (default 3) |
| `entityGroups` | Array of `{id, name, color, collapsed, members}` — active entity groups |
| `nextGroupId` | Auto-incrementing ID for new groups |
| `bulkSelectedIndices` | `Set<number>` — indices of shift-selected entities |
| `TOP_H`, `BOT_H`, `PAD_COL` | Layout constants: `44`, `64`, `20` (px) |
| `baseCELL` | Unzoomed cell size in pixels; actual `CELL = baseCELL × ZOOM_STEPS[zoomIdx]` |
| `panX`, `panY` | Viewport pan offset in pixels |

## Git Commit Conventions

Use [Conventional Commits](https://www.conventionalcommits.org/) style:

```
<type>(<scope>): <description>
```

Common types: `feat`, `fix`, `refactor`, `style`, `docs`, `chore`

If the commit was authored by Claude, use `claude` as the scope:

```
feat(claude): add line-of-sight follow behavior
fix(claude): correct bounce collision on diagonal mode
```

For human-authored commits the scope is optional or can describe the area changed:

```
feat: add new movement property
fix(editor): color picker not saving on cancel
```

## Planned Work (todo.md)

Active work-in-progress features and future plans are tracked in `todo.md`. Check it before starting new features to avoid duplication.

## Project History

Full commit history grouped by day is maintained in `development-history.md`. Update it when committing new work.
