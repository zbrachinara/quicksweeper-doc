# Score attack

Two players compete against each other to get the greatest possible score within some time.

## Lives and boards

When starting, both players are given a board, and select a position to begin in. When both players
have selected a position, the game begins and a timer starts. When a player has cleared a board,
they will be presented with a blank one of the same size. The timer will not pause for the player
who had cleared a board.

If a player reveals a mine, then their board is replaced with a new one, similar to if it were
cleared. The timer also will not pause for this event.

## Scoring

Score is awarded for every cell revealed, including those which were [revealed
recursively](./effects.md#recursive-reveal). Score is also awarded for clearing a board.

Combo score is awarded for successive reveals adjacent to one another. However, combo will not be
awarded for cells which were recursively revealed. It will be left unanswered for now whether an
adjacent cell is one which is next to the previous cell revealed or next to any cell revealed in the
current combo.

