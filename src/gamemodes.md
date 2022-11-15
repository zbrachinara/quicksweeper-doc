# Gamemodes

* [**Classic singleplayer**](./singleplayer.md)

A single player plays locally in order to clear a board without time constraint. Relevant statistics
include time and combo score.

* [**Area attack**](./area_attack.md)

Multiple players clear mines on the same board, claiming all areas they themselves have cleared.
Dying penalizes the players for a short time, and the game ends either on a timer or when the board
is clear. Players are then ranked based on the amount of cells cleared.

* [**Score attack**](./score_attack.md)

Two players on separate boards play against each other to gain the best score. When a player fails
too many times, the game ends for them and they must wait until the other player finishes in order
to have their scores compared. The player with the greatest score wins.

## Experimental: Not in version 1

* **Unnamed 1**

For each player, the board is created by an opponent, and the quickest player to finish after
all boards have been created wins

* **Free play**

A large (potentially unbounded) board is hosted on a central server. Like a 2015 .io game, players
are free to join and leave the board and play a game similar to [area attack](./area_attack.md).
There are some notable exceptions to this rule, however, such as that when someone's area gets
surrounded, their game ends.
