# Development History

## 2026-03-10

* feat(claude): enhance simulation UI with multicolumn entity list and improved layout; fix sizing issues in play area and log messages
* feat(claude): implement entity grouping functionality, allowing users to create, name, and assign properties to groups; enhance UI for bulk actions and selection mode
* fix(claude): resolve issues with entity movement and collision detection; ensure stopped entities resume in the correct direction and address save/load errors for out-of-space entities
* refactor(claude): streamline save and export functionality by introducing buildSavePayload and serializeEntity functions; enhance validation for entity properties including visual reactions and avoid types
* feat(claude): update simulation UI with multi-column entity list, improved footer layout, and enhanced header stats; fix terminology from "Game" to "Simulation" and adjust collision detection display
* feat(claude): implement avoidance behavior for entities, allowing them to steer away from specified targets and introduce new UI elements for avoidance type selection
* fix(claude): improve collision detection and enhance zoom functionality with reset option in simulation interface
* feat(claude): improve entity placement logic by adding overlap checks and fallback positioning, enhancing simulation accuracy and performance
* feat(claude): update entity properties and UI elements, enhance collision detection, and improve simulation configuration options

## 2026-03-08

* wip(claude): add resizing functionality to game area with new resize handles, implement minimum grid size inputs for simulation, and update zoom controls for enhanced user experience
* feat(claude): enhance entity line of sight rendering by improving border styles and fill effects for horizontal, vertical, and diagonal directions, resulting in better visual clarity during simulation
* feat(claude): enhance entity legend interaction by implementing event delegation for item selection and hover effects, improving user experience during simulation
* feat(claude): implement color picker for entity customization, add color swatches and selection functionality, and enhance entity editor with color options
* feat(claude): add visual reaction help modal and options, enhance UI with new section help buttons, and improve styling for better user interaction
* feat(claude): enhance UI with new animation for start button, update terminology from "game" to "simulation", and improve input styling for better user experience
* feat(claude): enhance overlap prevention by implementing path-based checks and residual guards to prevent entity collisions during simulation steps
* feat(claude): add log filter buttons for collision and vision events, enhance game log display, and improve logging for entity interactions during simulation steps
* feat(claude): add visual reaction options, save and load configuration, set default configuration
* feat(claude): enhance entity visibility and legend display by adding seen entity name styling and reintroducing vision computation in the draw cycle
* feat(claude): improve entity legend display by retaining previously hovered entity state, enhancing user interaction during simulation
* chore: update .gitignore to exclude temporary files, add new ai-models.md for AI tools documentation
* feat(Codex): add functionality to start a new game with default settings when the backspace key is pressed; update UI to reflect new control
* feat: implement line of sight for entities, allowing them to detect and display other entities within their view; update controls for stepping through simulation ticks
* feat: implement vision computation for entities to track seen entities during simulation steps and update legend display accordingly
* refactor: update collision property selection UI with a new dropdown design and improved button styles for better user experience
* fix: enhance collision detection to prevent overlapping entities during simulation steps
* fix: enhance path overlap detection in simulation by adding additional checks for entity interactions at consecutive time steps
* feat: add new game button to main menu, adjust default entity counts, and integrate game log into savegame functionality
* feat: enhance game logging functionality by adding log entry management and integrating logs into autosave and export features
* refactor: update layout and resizing behavior in simulation UI, changing flex direction and dimensions for improved usability
* feat: implement game log to display interaction events and enhance UI layout with new sections
* fix: ensure hover effect not only activates when simulation is running and update done.md with recent changes
* fix: remove redundant ESC key functionality to streamline game controls
* fix: ensure new game menu defaults are consistent and update input values for entity counts
* feat: add initial game speed setting in New Game menu and update game options menu behavior
* feat: implement hover effect for entities, displaying a white crosshair on mouseover
* feat: add CLAUDE.md for project guidance, detailing architecture, movement properties, UI layout, and key constants
* feat: add todo.md for work in progress and future plans, detailing features, behaviors, player character, refactoring, and deployment strategies
* feat: update version display to reflect current version dynamically

## 2026-03-07 — Initial setup

* feat: improve game controls and ESC button behavior for better user experience
* feat: add game options screen for adjusting simulation settings and entity controls
* feat: enhance collision detection and path handling for entities
* feat: update ESC button functionality to open options instead of restart
* feat: initial commit
