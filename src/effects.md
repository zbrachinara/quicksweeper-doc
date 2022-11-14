# Board effects

The board is a global resource whose properties and getters may be constricted based on gamemode.

## Cell reveal

A player can reveal a cell, which will either yield a mine or a blank cell. If it is a mine, the
game will end for that player. If it is empty, the player will be given knowledge about the state of
that cell, and all the cells next to it if it is known that there are no mines next to those (for the
sake of convenience).
