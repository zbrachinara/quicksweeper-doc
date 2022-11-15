# Players

## Properties

A player is an entity with properties, which can either be transient or specific. Transient
properties apply to the player no matter the gamemode, while specific properties are properties
which are added by the gamemode.

The transient events are:

* Position: The last known position the cursor takes
* Board state: The state of the board the player knows.

Some examples of specific events include [TODO]

Similarly, Each player has access to one set of transient controls. These are:

* **Directional controls**: The ability to modify their position
* **Check cell**: The ability to reveal cells
* **Flag cell**: The ability to flag cells.

And specific controls may be added based on gamemode.

### Property deltas and client/server

Gameplay, from an implementation perspective, is the process of keeping the state between client and
server, and on the serverside client states with each other, consistent. In order to do this, the
client and server, when an "event" occurs, will send messages to each other that contain property
deltas. A property delta is a description of the changes to properties in the time between messages. 

## Plexing

Multiple players can be plexed into one game over network or on a single machine by individual sets
of controllers, although some gamemodes may be limited to network only to hide information relevant
to the game mode.
