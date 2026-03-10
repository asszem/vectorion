# Work in progress

* feat: assign entire groups to Follow / Avoid actions


# Tasks to do

## New Simulation Menu updates
* rework the New Simulation menu
* change wording to Max Entity Size, Play Area Size, Max Entity Speed, 
* add toggle: Line of Sight display
* create Entity groups
* Introduce Entity Templates - that holds all available options for an entity
* User can create, modify, save and load entity templates (json)
* Game config menu to have 2 section: general settings and entity settings
* General settings to have sim speed, display trail, etc. settings.
* Entity setting: Add new entity from scratch
* Update save/load sim config, that includes all entity templates
* Initial entity placement shape: Circle, Random, Expanded (as far as possible)

## Simulation Options menu updates
* Display options (Speed trail, Line of Sight display)
* Graphics settings: Glow effect, Trail, Line of sight
## Log updates

## Save / load updates

## Play area updates
* follow selected entity if it leaves visible play area
* resize play area viewport, adjusting zoom level accordingly

## Entitiy list updates
* feat: multi edit entities
* feat: multi column entities list according to available space

## Footer updates
* redesign the buttons and the label texts to look more concise 

## Collision detection 
* fix: entities should only change direction when they were connected directly. If the collision detection triggers, change their speed? or draw them until they would overlap and then change their direction?

## Minor or undecided changes

## Misc changes, not directly related to gameplay
* misc(cursor-vim): map Ctrl-O to jump to location

# Future plans

## Entity properties that determine their actions
* feat: velocity - entities can change their speed. 
* HP - collision reaction, can be devoured or destroyed if higher hp
* Speed - max speed
* Energy - determines max speed
* Recovery - to recover energy
* Flee / Catch - speed up towards / from enemy

## Rewind simulation
* Everything can be replayed or tick reverted.

## Behaviours

* add Behaviour: Follow \[Target]
* add Behaviour: Avoid \[Target]
* add Behaviour: Stop \[Ticks]
* Add Behaviour: Change Direction \[Opposite]
* Add Behaviour: Change Reaction \[Reaction]
* Add Behaviour: Change Speed \[Speed]

## Tick sequence refactor

1. Vision - line of sight in direction
2. Decision - select behaviour
3. Action - execute behaviour

* document

## Controllable Player character

* Create a 1x1 character
* It can be moved by cursor keys or keypad
* It can move to every direction with its speed
* The collision rule can be set to be anything

## Refactor

* Select a more efficient programming language
* Separate javascript, html and css files

## Deploy
* Deploy to github.io
