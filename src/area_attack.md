# Area attack

2-4 players compete in a timed match to claim the most area on a single board. 

## Area

A player's area is defined as a region of the board *only* containing the cells which the player has
uncovered, which is not necessarily contiguous. The state of a cell contained in a player's area is
not visible to opponents, except for that the cell is owned in that area. 

## Starting

The game begins with a blank board. All players will pick starting points from which to begin
clearing, for which a minimum distance will be enforced (consequently, a larger board is better to
allow for more variation in starting positions). When all players have selected and confirmed a
starting position, a board will be generated in such a way that the players do not have areas which
share borders. After this stage, the game will have begun.

## Stages

The game runs on a timer which determines when the game ends and what stage the game is in.
Different stages will determine different board effects, which influence the strategy of the game.
To accomodate for different skill levels, however, the total amount of area claimed should also
advance the game state.  While the game will end no matter what when the timer runs out, the game
can also end before if the entire board is clear. 

### Stage 1: Default mechanics

Players begin claiming area without restrictions. When a player uncovers a mine, they are penalized
by being frozen for some time. In this time, the player is not given any new information about the
board and not allowed to execute any new actions.  On the other hand, opponents will be able to see
that the player is frozen. After the player is unfrozen, the mine will be revealed on the board, and
for the rest of the game it will not be allowed to be revealed.

### Stage 2: Attack (after 3 minutes)

In this stage, uncovering a mine will incur an different penalty: A region of cells around the mine
will be regenerated and become unclaimed, allowing for anyone to attempt claiming it. This mechanic
can further penalize mistakes, but, as the name of the stage suggests, it is mostly there for
attack. Lack of freezing should encourage the use of this mechanic as well. As with the previous
effect, a revealed mine will be displayed and not allowed to be checked again.

### Stage 3: The final stage: Lock (after 6 minutes)

All previous effects apply, but now only cells that are adjacent to the player's area can be
uncovered by that player.