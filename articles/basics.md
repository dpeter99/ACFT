# The basics of a mod

## The idea
We want to add new content to the game. Yes some stuff can be added by using the vanilla mechanics but those are extremly limited. So we want to use Java the language MC is written in.
To make it easier we use Forge witch provides a lot of usefull functons and classes to make extending the game eas easy as possible.

## Registries
Registries are minecraft's way of keeping a list of all the tings that exists. So things like: Blocks, Items, Mobs, etc.. All registries are closed after the game loads so we have to add our new items in there while the game is loading up. For this forge provides functions that get called when wach registry is being loaded up.
There is also a way for us to make new registry types (like spells) and other mods can also add items to these so people can make extension mods (if we allow it by making the classes awailable).