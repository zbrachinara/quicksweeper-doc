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

## Communication
Messages from client to server:
"x\ny"
x and y are the coordinates of the square that the player is revealing, as base-10 strings. \n is a newline. For example: "10\n9"

Messages from server to client:
When a player joins, they are given an initial message with the parameters of the game. This message is "multiplayer minesweeper\nb\np", where b is the boardsize as a base-10 integer, and p is the probability that a square is a mine.
All subsequent messages have the following form:
"x\ny\nbd"
x and y are coordinates in base 10, representing the location of the event. "\n" is the newline character. b is a one-byte code indicating the type of event. d is the data associated with the event.

codes:
'j':
    A new player has joined the game. x and y are currently unused.
    d: player name
'c':
    The square at position (x,y) is revealed.
    d: the number of mines adjacent to the square.
    This message typically comes as a reply to a guess by the client.
'o':
    Another player has claimed the square at (x,y).
    d: the name of the other player
'f':
    A player has been frozen by a mine at position (x,y).
    d: the name of the player. Could be yourself.
'm':
    A message directly to the user - for example, if they try to make a selection while frozen.
    d: the message

Tentative:
's':
    
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
attack. Lack of freezing should encourage the use of this mechanic as well.

In addition, players will no longer be able to clear mines everywhere, instead only being able to
clear cells that are adjacent to the player's area.

### Stage 3: The final stage: Lock (after 6 minutes)

All previous effects apply, and after a minute the game ends and placement is determined. 