# Gamemodes

* [**Classic singleplayer**](./singleplayer.md)

A single player plays locally in order to clear a board without time constraint. Relevant statistics
include time and combo score.

* [**Area attack**](./area_attack.md)

Multiple players clear mines on the same board, claiming all areas they clear. Hitting a mine
penalizes players without elimination, and the game ends either on a timer or when the board is
clear. Players are then ranked based on the amount of cells cleared.

* [**Score attack**](./score_attack.md)

Two players on separate boards play against each earn score. When a player fails too many times, the
game ends for them and they must wait until the other player finishes. The player with the highest
score wins.

## Experimental (not in version 1):

* **Enemy setup**

Each player determines the placement of mines for the board of one other player. Once all the
boards are set, the game starts. The player that finishes soonest wins.

* **Free play**

A large (potentially unbounded) board is hosted on a central server. Like slither.io or agar.io,
players are free to join and leave the board and play a game similar to [area
attack](./area_attack.md). There are some notable exceptions to this rule, however, such as that
when someone's area gets surrounded, their game ends, and their area becomes unclaimed and reset.

* **Stacked mines**

Cells with mines can be weighted variably, so that even if one cell has one neighboring cell
containing mines, it may contain multiple mines.

* **Tunneling mines (or: whack-a-mine)**

There are a (potentially reduced) number of mines that periodically move collectively. Uncovered
cells will have their numbers changed accordingly. No mine will move to an uncovered or flagged
cell, nor to a cell directly adjacent to an uncovered cell. A flagged mine won't move. Flag all
mines to win.
