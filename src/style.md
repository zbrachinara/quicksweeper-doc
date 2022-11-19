# Style guide

Quicksweeper is played on an isometric field-top view of the board. For the default field,
predominant colors are black with neon white, blue, and red as accents. Additional colors used as
identification for players are also used as accent.

## Cell

A cell is a square tile with a little less than half as much thickness as the width. Cells are tiled
across the board with a slight gap between them, and with their thickness on the axis perpendicular
to the plane of the camera (that is, they are laid face up on the "floor"). For blank tiles, the
cell is transparent with white accent on all its edges.

The top face is the face of the cell that is closest to the plane of the camera.

When revealed, the faces fill with a color depending on what type of cell is revealed. For a mine,
the cell fills with red, and a mine appears on its top face, indicating the end of the game. If it
is blank, the cell fills with the team's accent color, and, depending on whether or not there are
mines neighboring that cell, a number appears on the top face in white.

## Player

The player is drawn as an transparent square with edges accented by the player's team color. They
float on a plane slightly above the top face of the board. When viewing from the isometric
perspective, the thickness of the accent should cover the gap between the cells, but should not
intrude on the cells themselves (although it may intrude on their accents)
