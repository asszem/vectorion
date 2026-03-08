# 2026-03-08 -

* feat: start a new game when backspace key is pressed with default settings

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
