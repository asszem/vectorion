# 2026-03-10

* fix: stoped entities will resume movement to the opposite direction they got bumped from
* feat: Vision: Avoid
* fix: save/load simulation entity out of space errors
* refactor: footer and header menu item repositioning
* fix: initial and running collision detection (works well at this point)
* fix: zoom, play area size, viewport size

# 2026-03-08

* feat: resizable play area, set in initial config
* play area zoom / entity display size
* feat: custom color for entities
* feat: move Help modals next to Collision and Visual reaction 
* feat: rename Game to Simulation everywhere
* feat: save/load Simulation configuration on New Simulation window
* feat: set current Simulation Config as Default (in localStorage)
* fix: add enable/disable entity trail option to Paused Game Options menu
* feat: start a new game when backspace key is pressed with default settings
* fix: collision detection when entity is stopped, nothing should be able to overlap it
* feat: filterable log messages, log for vision, hoverable log messages
* fix: display crosshair and line of sight when the simulation runs and user hovers over entity list
* fix: entity not seeing other entity, even if it is partially in its line of sight
* fix: seen other entity display font barely visible, make it bigger
* fix: change wording from Game to Simulation

# 2026-03-07 - Initial game setup, Collision reactions, save/load functions, LOS

* epic: add Vision to entities
* feat: at the beginning of each tick, each entity towards its movement direction has line of sight until the end of the game area
* feat: if there is another entity in its line of sight, it will see that entity.
* feat: the entity list should display the name of the entity being seen
* feat: if there is no entity, nothing should be displayed
* fix: improve collision detection
* feat: rename properties to Reactions. Destroy, Bounce, Stop, Devour, Change
* feat: game log - display interaction events - "Entity 1 Destroyed Entity 2 at Tick 231"
* feat: game log - add game log to savegame (localStorage and json file save)
* feat: hover over entity displays white crosshair
* fix: hover is displayed even when simulation is stopped
* feat: initial game speed set in New Game menu
* fix: remove the O option, Esc and Game name click should open the Game Options menu
* fix: new game menu should have the same default values, regardles of any changes
