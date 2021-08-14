# Printable Tabletop Mapping Kit
Create maps for Pen&amp;Paper RPGs or other tabletop games, in an economical style. For fancy output, import your own ground texture. This project contains a tileset (tsx file) and source files for creating the tileset. The tileset is meant to be used in [Tiled Map Editor](https://www.mapeditor.org/).
![screenshot](https://github.com/poikilos/PrintableTabletopMappingKit/raw/master/screenshot.png)

## Use
This tileset differs from most, in that it is "subtractive." The "Build" terrains covers everything but the walkable area. The "Dig" terrains. That means that you should have a ground texture and/or grid. That can be done using the following directions. Another difference is that the "synthetic grid" (gray in picture) is 2x2 Tiled Map Editor units--grid mode (the dotted black lines) should be turned off when using this, and the grid texture (described below) should be used for in-game measurements. The synthetic grid allows for drawing most helpful shapes; it also means that the paint brush is 1x1 in synthetic grid units. These grid squares would represent 5x5ft in most tabletop games. Summary of steps below: fill a layer with ground texture, fill another layer with double-spaced synthetic grid lines, fill another layer with "Build" terrain, then use "Dig" terrain to draw walkable areas. Place props on a 4th layer (more if offset is needed).
* Install Tiled Map Editor
* Open Tiled Map Editor
* New Map
* Open File, choose ptmk-64x64.tsx
* Go back to map tab (the .tmx file)
* Make sure the "Layers" tab is selected on the right
* IF you ever mess up your user interface (lose panels I describe in this guide), reset all your Tiled settings by deleting (/.config/mapeditor.org/tiled.conf on Linux or macOS; On Windows, the may be in %APPDATA%)
* Turn off the grid since the kit makes a special 2 unit per line grid that allows automatic cornering (Click "View," "Show Grid" unless it is already unchecked).
* Double-click the layer name and change it to **"Ground"**
  * In the "Tilesets" tab, choose a plain white square for economical printing, or choose any terrain texture you want. This will be the texture that "shows through" when you cut out the area where characters can walk.
  * Fill the entire "Ground" layer, by choosing Bucket Fill Tool (F) then clicking the background
  * Click the unlocked symbol by "Ground" layer to change it to locked.
* In the menu bar click "Layer," New, Tile Layer, type **"Grid"** to name it.
* Click the "Tilesets" tab at bottom right
  * Drag to select the grid (2x2 area from ID 3 to ID 20)
  * Fill the entire "Grid" layer, by choosing Bucket Fill Tool (F) then clicking the background
    (if you do not see the grid lines, try zooming in)
  * Click the unlocked symbol by "Grid" layer to change it to locked.
* In the menu bar click Layer, New, Tile Layer, and type **"Walls"** to name it.
  * In "Terrain" tab, choose the "Build" terrain for the terrain type you want, such as "Build Sharp Wall" or "Build Cave" (make a separate layer for each so that the corners smooth automatically).
  * ~~Fill the entire layer, by choosing Bucket Fill Tool (F) then clicking the background
  if this doesn't work, you may need to~~ Manually choose the wall material, which is the bottom left tile of the terrain, such as ID 85 for cave, or ID 80 for sharp wall--whatever is below the bottom right cutout of the tileset region.
* Click the "Terrains" tab at the bottom right
  * Choose a "Dig" terrain (or the matching "Build" to undo), and paint as needed to make your level
* To make exits (leave open ended area without black outline), go to Tilesets tab and click the plain white color (or whatever tile matches the "Build" terrain)
* Make a new layer and call it **"Props."** Place any props on this layer so Walls layer doesn't become broken apart.
  * Props (such as circles or squares which can represent pillars or tables) can be chosen in the "Tilesets" tab (for objects larger than 1x1, you can select the whole object at once), and then placed using the Stamp tool.
  * To place objects with an offset (anywhere between grid lines instead of on them), put the object on a new layer then use the layer offset tool (click the 4-arrow button or press 'm' key, then drag--this affects whole layer, so place offset objects on separate layers)
  * For props where edges must be connected to (obscured by) walls, such as gates, make an alternate third layer named **"Obscured Props"** and drag it below the "Walls" layer in the Layers list.

### Print (or save image for other reason)
  * For saving reduced size image for screen use (such as web), you can change the zoom (Hold Ctrl and use mouse scroll wheel or + and -) first to make it appear the size you want.
  * click File, "Export As Image,"
  * Choose a location and name (make sure "Draw Tile Grid" is unchecked)
  * Normally you can uncheck "Use current zoom level," but if you zoomed for screen use, (such as for display on screens, or if you are printing smaller than 1 grid square per inch) you can check it if you have zoomed out to an acceptable scale (for example, if you use a 64x64 tileset, the synthetic grid lines are spaced by 128px--so if you plan to scale it down later so there are 6 grid lines per inch, you can zoom to 50% with this option checked you still get 384 dpi and a much lower file size than if unchecked).
  * Open the image you saved in a different program (IrfanView recommended for Windows, Gwenview or Okular for Linux--Ctrl P then Properties to see size), then print using that program.

### Tips
#### Using the ptmk tileset with Tiled Map Editor
* most passageways for tabletop RPGs, especially where battles will occur, should be at least 2 grid marks (10ft) wide, to allow creatures to move around each other.
* To draw 1x1 (.5x.5 synthetic grid squares) instead of 2x2 (1x1 synthetic grid squares) with the Terrain Brush, hold Ctrl key. Name layers to help you keep track later (recommended: put "offset" in the name of offset layers)
* Objects made of "Build" or "Dig" terrain that are not just a plain square but fewer than 2 squares in any dimension must be constructed piece by piece out of corners and walls using the "Tilesets" tab.
* If edges of wall become disconnected, obscure then redraw them using the Build and Dig terrains (neither actual Erase tool nor Stamp tool are needed, but you can use Stamp if you need different types of corners on the same map). If you still have trouble, make sure the obscured area is painted using the matching terrain (for example, for Caves, make sure background is the "Build Cave" terrain and then you can successfully draw with the "Dig Cave" terrain).

## Known Issues
* Include natural-looking tiles for printing fancy maps

## Developer Notes
### Why Tileset is Inverse of Standard
I tried setting up subtractive painting in Tiled Map Editor using the normal way of doing tilesets (see terrain blocks using the Liberated Pixel Cup standard such as [LPC Terrain Repack](https://opengameart.org/content/lpc-terrain-repack)), but that did not work, even with various hacky setups in Tiled's terrain designer. I had to design all terrains with alpha opposite of normal for this to work. I could have used a ground texture with walls (see pits in LPC Terrain Repack), but then the grid would have to be embedded in every tile, making lines non-optional and tiles difficult to maintain. The inverted setup I created for Printable Tabletop Mapping Kit seems like the only way to make drawing this style of map in Tiled this easy for the user.

## License
(Author: Jake Gustafson aka poikilos)
* Data license: This work is licensed under the Creative Commons Attribution-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-sa/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.
* Code license: no code is planned to be in this repository, but if so, see [LICENSE](https://github.com/poikilos/PrintableTabletopMappingKit/blob/master/LICENSE) for license.
