# Work in Progress
- feat: hover over entity displays white crosshair
- feat: initial game speed set in New Game menu
- fix: game options menu to show existing entities with the ability to change their numbers
- fix: remove the O option, Esc and Game name click should open the Game Options menu
- feat: rename properties to Reactions. Destroy, Bounce, Stop, Devour, Change
- feat: game log - display interaction events - "Entity 1 Destroyed Entity 2 at Tick 231"
- feat: game log - add game log to savegame (localStorage and json file save)

# Future plans

## Vision
- add Vision to entities

## Behaviours
- add Behaviour: Follow [Target]
- add Behaviour: Avoid [Target]
- add Behaviour: Stop [Ticks]
- Add Behaviour: Change Direction [Opposite]
- Add Behaviour: Change Reaction [Reaction]
- Add Behaviour: Change Speed [Speed]

## Tick sequence
1. Vision - line of sight in direction
2. Decision - select behaviour
3. Action - execute behaviour


## Player character
- Create a 1x1 character
- It can be moved by cursor keys or keypad
- It can move to every direction with its speed
- The collision rule can be set to be anything

## Refactor
- Select a more efficient programming language
- Separate javascript, html and css files

## Deploy
- Deploy to github.io