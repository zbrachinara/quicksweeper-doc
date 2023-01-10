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

* [**Number Guess**](./number_guess.md) (for Sam)
Guess the number.

## Experimental (Not to be implemented in version 1):

* **Enemy setup**

Each player determines the placement of mines for the board of one other player. Once all the
boards are set, the game starts. The player that finishes soonest wins.

* **Free play**

A large (potentially unbounded) board is hosted on a central server. Like slither.io or agar.io,
players are free to join and leave the board and play a game similar to [area
attack](./area_attack.md). There are some notable exceptions to this rule, however, such as that
when a player selects a single mine, their game ends, and their area becomes unclaimed and reset. Players also lose for not making enough progress in a certain amount of time, to encourage fast, exciting play and prevent the game from being clogged up with players who have nothing to do but don't want to lose.


* **Capture the Flag**

Two or more teams each have a flag. The goal of the game is to collect all flags. Play proceeds as in stage 2 of area attack: activating a mine causes neighboring squares to reset. When a flag is in a team's territory, that team may move the flag to a neighboring square. This acts as if a mine was activated. To move the flag again, the team must reclaim the area surrounding the flag.


* **Teams**

There are two teams playing on a large board. Each starts on their own side. Players can see the numbers in all squares their team has claimed. Players may select any square adjacent to one of their team's squares. Activating a mine causes neighboring squares to reset, and freezes the player who selected the mine. Each team is trying to claim the entire board for themselves.

* **Stacked mines**

Cells with mines can be weighted variably, so that even if one cell has one neighboring cell
containing mines, it may contain multiple mines.

* **Continuous Mines**

The board is a subset of R^2 instead of Z^2. Mines are disks of radius 1. Mines either can't overlap, or can (stacked mines). Guesses are points. Guessing inside of a mine is a loss. For guesses outside of a mine, the total area of mines enclosed in the disk of radius 1 surrounding the point is returned.

* **Tunneling mines (or: whack-a-mine)**

There are a (potentially reduced) number of mines that periodically move collectively. Uncovered
cells will have their numbers changed accordingly. No mine will move to an uncovered or flagged
cell, nor to a cell directly adjacent to an uncovered cell. A flagged mine won't move. Flag all
mines to win.

* **3D**

The board has three (or more dimensions)

* **Arbitrary graph**

Mines are placed at vertices of a graph. Guesses are vertices. Guessing a mine results in a loss. Guessing a non-mine reveals the number of mines connected to that vertex.