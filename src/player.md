# Players

A player has exactly one state in a base game: Its position. Additional properties can be added by
specific gamemodes, but the position is guarantee. Multiple players can be plexed into one game
over network or by controls, although some gamemodes may be limited to network only (to hide
information, for example).

Each player has access to one set of controls. These are:

* **Directional controls**: The ability to modify their position
* **Check cell**: The ability to reveal cells
* **Flag cell**: The ability to flag cells.

These events individually may or may not be propogated through to other players depending on the
gamemode.
