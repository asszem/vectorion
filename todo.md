# Work in Progress

* fix: display crosshair and line of sight when the simulation runs and user hovers over entity list
* fix: entity not seeing other entity, even if it is partially in its line of sight
* fix: seen other entity display font barely visible, make it bigger
- Start a new game when backspace key is pressed with default settings


## Minor or undecided changes

* fix: game options menu to show existing entities with the ability to change their numbers

# Future plans

## Vision

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
