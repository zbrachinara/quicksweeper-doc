# Style guide

Quicksweeper will be played with an isometric field-top view of the board. For the default playing
field, predominant colors will be black with neon white, blue, and red as accents. Additional
colors used as identification for players will also be used for accent.

## Cell

A cell will be a square tile with a little less than half as much thickness as the width. Cells will
be tiled across the board with a slight gap between them, and with their thickness on the axis
perpendicular to the plane of the camera (that is, they are laid face up on the "floor"). For blank
tiles, the cell will be transparent with white accent on all its edges.

The top face is the face of the cell that is closest to the plane of the camera.

When revealed, the faces will fill with a color depending on what type of cell is revealed. For a
mine, the cell will fill with red, and then a mine will appear on its top face, indicating the end
of the game. If it is blank, the cell will fill with the team's accent color, and, depending on
whether or not there are mines neighboring that cell, a number will appear on the top face.

## Player

The player is drawn as an transparent square with edges accented by the player's team color. They
will float on a plane slightly above the top face of the board. When viewing from the isometric
perspective, the thickness of the accent should cover the gap between the cells, but should not
intrude on the cells themselves (although it may intrude on their accents)
