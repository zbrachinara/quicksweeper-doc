# Scoring

Score is awarded for every cell revealed, including those which were [revealed
recursively](./board.md#recursive-reveal). Score is also awarded for clearing a board.

Combo score is awarded for successive reveals adjacent to one another. However, combo will not be
awarded for cells which were recursively revealed. It will be left unanswered for now whether an
adjacent cell is one which is next to the previous cell revealed or next to any cell revealed in the
current combo.
