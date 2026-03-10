# Work in Progress

* fix: zoom, play area size, viewport size

## Follow
* For some reason, the following works now.

Update the behaviour of the entity so if the followed entity is seen, the following is moving towards its direction until collision.
If followed entity is not seen by follower, then follower should stop reduce Movement Speed to zero. Introduce a new entity property: Detection speed, which can be a number from 1-max speed. By default, it should be the same for every entity as its movement speed. 
4. Turn direction (clockwise)
5. Use as many turns in a tick as the speed of the entity
6. If marked entity is seen during turn, move towards it

## Misc changes
* misc(cursor-vim): map :E to saveAll
* misc(cursor-vim): map Ctrl-O to jump to location
* misc(git-bash): install goto
* misc(vscode): install vscode, import all settings from Cursor
* misc(cursor): save settings.json to .mydotfiles

## Minor or undecided changes
* change wording from Game to Simulation
* rework the New Simulation menu
* Introduce Entity profiles - that holds all available options for an entity
* User can create, modify, save and load entity profiles (json)
* Game config menu to have 2 section: general settings and entity settings
* General settings to have sim speed, display trail, etc. settings.
* Entity setting: Add new entity from scratch
To be continued 

## Play area
* follow selected entity if it leaves visible play area

# Future plans


## Rewind 
Everything can be replayed or tick reverted.

## Behaviours

* add Behaviour: Follow \[Target]
* add Behaviour: Avoid \[Target]
* add Behaviour: Stop \[Ticks]
* Add Behaviour: Change Direction \[Opposite]
* Add Behaviour: Change Reaction \[Reaction]
* Add Behaviour: Change Speed \[Speed]

## Tick sequence

1. Vision - line of sight in direction
2. Decision - select behaviour
3. Action - execute behaviour

## Player character

* Create a 1x1 character
* It can be moved by cursor keys or keypad
* It can move to every direction with its speed
* The collision rule can be set to be anything

## Refactor

* Select a more efficient programming language
* Separate javascript, html and css files

## Deploy

* Deploy to github.io
