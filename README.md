# PrintableTabletopMappingKit
Create maps for Pen&amp;Paper RPGs or other tabletop games, in economical or fancy styles. This is the tileset (tsx file) and source files for creating the tileset. The tileset is meant to be used in [Tiled Map Editor](https://www.mapeditor.org/).

## Use
This tileset differs from most, in that it is "subtractive." That means that you should have a ground texture and/or grid. That can be done using the following directions. Another difference is that the grid is 2x2 Tiled units--the dotted black lines should be ignored, and the grid texture (described below) should be used for in-game measurements. This allows for drawing most helpful shapes; it also means that the paint brush is 1x1 on the synthetic grid (which represents 5x5ft in most tabletop games).
* Install Tiled Map Editor
* Open Tiled Map Editor
* New Map
* Open File, choose ptmk-64x64.tsx
* Go back to map tab (the .tmx file)
* Make sure the "Layers" tab is selected on the right
* IF you ever mess up your user interface (lose panels I describe in this guide), reset all your Tiled settings by deleting (/.config/mapeditor.org/ on Linux or macOS)
* Click "View," "Show Grid" unless it is already unchecked.
* Double-click the layer name and change it to "Ground"
  * In the "Tilesets" tab, choose a plain white square for economical printing, or choose any terrain texture you want. This will be the texture that "shows through" when you cut out the area where characters can walk.
  * Fill the entire "Ground" layer, by choosing Bucket Fill Tool (F) then clicking the background
  * Click the unlocked symbol by "Ground" layer to change it to locked.
* In the menu bar click "Layer," New, Tile Layer, type "Grid" to name it.
* Click the "Tilesets" tab at bottom right
  * Drag to select the grid (2x2 area from ID 3 to ID 20)
  * Fill the entire "Grid" layer, by choosing Bucket Fill Tool (F) then clicking the background
  * Click the unlocked symbol by "Grid" layer to change it to locked.
* In the menu bar click Layer, New, Tile Layer, and type "Walls" to name it.
  * In "Terrain" tab, choose the "Build" terrain for the terrain type you want, such as "Build Sharp Wall"
  * Fill the entire layer, by choosing Bucket Fill Tool (F) then clicking the background
* Click the "Terrains" tab at the bottom right
  * Choose a "Dig" terrain (or the matching "Build" to undo), and paint as needed to make your level
* To make exits (leave open ended area without black outline), go to Tilesets tab and click the plain white color (or whatever tile matches the "Build" terrain)

### Tips
* 1x1 objects such as Pillars and square tables can be placed using the "Tilesets" tab
* To draw 2x2 instead of 3x3, hold Ctrl key while drawing with Terrain Brush.
* Tables that are not just a plain square but fewer than 2 squares in any dimension must be constructed piece by piece using the "Tilesets" tab.

## Known Issues
* Fewer tiles would be needed in tileset if each tile was made up of 4 quarter-tile graphics (grid spacing would have to be 2x2 Tiled Map Editor units)
  * Far fewer tiles may be needed in tileset if each tile was made up of 9 third-tile graphics (grid spacing would have to be 3x3 Tiled Map Editor units)


## License
(Author: Jake Gustafson aka poikilos)
* Data license: This work is licensed under the Creative Commons Attribution-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-sa/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.
* Code license: no code is planned to be in this repository, but if so, see [LICENSE](https://github.com/poikilos/PrintableTabletopMappingKit/blob/master/LICENSE) for license.
