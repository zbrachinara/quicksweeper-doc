# Players

## Properties

A player has an entity with properties, which can either be global or specific. global properties
apply to the player no matter the [gamemode](./gamemodes.md), while specific properties are
properties which are added by the gamemode.

The global properties are:

* Position: The last known position the system cursor hovered over. Indicated by a crosshair on the
  board.
* Board state<sup>*</sup>: The state of the board the player knows.

Some examples of specific events include [TODO]

Similarly, each player has access to one set of global controls. These are:

* **Translational controls**: The ability to modify their position
* **Check cell**: The ability to reveal cells
* **Flag cell**: The ability to flag cells.

And specific controls may be added based on gamemode.

<sub> *The board state can have specific properties, but it itself is required in every game, so we
include it here. </sub>

### Property deltas and client/server

Gameplay, from an implementation perspective, is the process of keeping the state between client and
server, and on the serverside client states with each other, consistent. In order to do this, the
client and server will send messages to each other on their respective events that contain property
deltas. A property delta is a description of the changes to all the properties the client has access
to in the time between messages. 

## Plexing

Multiple players can be plexed into one game over network or on a single machine by individual sets
of controllers, although some gamemodes may be limited to network only to hide information relevant
to the game mode.
