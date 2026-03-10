# Work in Progress

* feat: Vision: Avoid
* feat: velocity - entities can change their speed. 



## Misc changes
* misc(cursor-vim): map Ctrl-O to jump to location

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

## Entity properties that determine their actions
- HP - collision reaction, can be devoured or destroyed if higher hp
- Speed - max speed
- Energy - determines max speed
- Recovery - to recover energy
- Flee / Catch - speed up towards / from enemy

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
