# Area attack

2-4 players compete to claim the most area on a single board. 

## Area

A player's area is defined as the region of the board *only* containing the cells which the player
has uncovered. The area is not necessarily contiguous. The state of a cell contained in a player's
area is not visible to opponents, except for that the cell is owned in that area. 

## Starting

The game begins with an untouched board. All players will pick starting points from which to begin
clearing, for which a minimum distance will be enforced (consequently, a larger board is better to
allow for more variation in starting positions). When all players have selected and confirmed a
starting position, a board will be generated in such a way that the players do not have areas which
share borders. After this stage, the game will have begun.

## Penalty

When a player uncovers a mine, they are penalized by being frozen for some time. In this time, the
player is not given any new information about the board and not allowed to execute any new actions.
On the other hand, opponents will be able to see that the player is frozen. After the player is
unfrozen, the mine will be revealed on the board.

## Time

The game runs on a timer which determines when the game ends and what stage the game is in.
Different stages will determine different board effects, which influence the strategy of the game.
While the game will end no matter what when the timer runs out, the game can also end before this if
the entire board is clear. 

Relevant stages:

* [TODO]
