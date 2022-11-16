# Board effects

The board is a global resource whose properties and getters may be constricted based on gamemode.

## Cell reveal

A player can reveal a cell, which will either yield a mine or a blank cell. If it is a mine, the
game will end for that player. If it is empty, the cell will display the number of mines that are
next to it, or remain blank if there are no neighboring mines. Such cells will be called "free
cells". 

### Recursive reveal

When a free cell is revealed, all of its neighboring cells will be revealed in the same way as well.
For games in which sequence matters (e.g. [Area Attack](./area_attack.md)), cells are revealed in
the order of the recursion (that is, the farther a cell is from the original cell revealed by the
player, the later it is revealed, or "owned"). 

