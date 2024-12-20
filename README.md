# Printable Tabletop Mapping Kit
Create maps for Pen&amp;Paper RPGs or other tabletop games, in an economical style. For fancy output, import your own ground texture. This project contains a tileset (tsx file) and source files for creating the tileset. The tileset is meant to be used in [Tiled Map Editor](https://www.mapeditor.org/).
![screenshot](https://github.com/poikilos/PrintableTabletopMappingKit/raw/master/screenshot.png)

## Related Projects
* Top Down Dungeon Pack CC0 by Screaming Brain Studios for Tiled: <https://opengameart.org/content/top-down-dungeon-pack>
* Scribble Dungeons CC0 by Kenney: <https://opengameart.org/content/scribble-dungeons>

## Main features
* Subtractive: Start with entire map filled with wall terrain, then cut a path through the "walls" to show the terrain underneath!
  - Tint the "Walls" any color (default is white to save ink) using Tiled.
* Grid can be on its own layer: Put any terrain under it.
  - Tint the grid lines white/black/other color using Tiled Map Editor.
  - Tint the default white terrain any color using Tiled Map Editor
  - Draw any type of wall over the grid to cover those parts.
* Grid is double size: Cut natural shapes more easily and use fewer tiles for creating natural shapes.
* Export your own resolution from the SVG file using Inkscape!
* High dpi for printing! However, resolution is typically higher than that even, since a dungeon is typically scaled down to less than 1/60 scale to fit on one page of a book. Examples:
  * 75 x 75 = 300dpi at 2 "gpi" (grid lines per inch) as in 1/2 of 1/60 scale (1/120 scale). The same tileset becomes 600dpi at 4 gpi (as in 1/4 of 1/60 scale = 1/240 scale), since 4 gpi is 8 tiles per inch (8 * 75 = 600). Such scales typical for fitting a large dungeon on one page of a book.
  * 150 x 150 = 300dpi at actual size. 4/more tpi (4/more tiles per inch = 2/more grid lines per inch) results in 600+ dpi (2/fewer tpi for 300 dpi). Multiply 150 by 16 tiles, so export at 2400 resolution.
  * Actual 1/60 scale would have 300x300 tiles: For printing 1:60 scale tactical grids, 300 or 600 dpi is recommended (300x300 version is 600 dpi as in 600 per grid line, so export as 4800px as in 300*16, then res is doubled to 600 px per tile since each grid square is 2 Tiled tiles. Typically you don't need to print at real 1/60 scale in your publication, just print the grid lines to illustrate the scale (such as to help the GM draw it on a battle mat at the real 1/60 scale). You would only need 4800x4800 to print actual-size tactical maps at 600 dpi (2400x2400 for 300 dpi).

## Use
This tileset differs from most, in that it is "subtractive." The "Build" terrains covers everything but the walkable area. The "Dig" terrains. That means that you should have a ground texture and/or grid. That can be done using the following directions. Another difference is that the "synthetic grid" (gray in picture) is 2x2 Tiled Map Editor units--grid mode (the dotted black lines) should be turned off when using this, and the grid texture (described below) should be used for in-game measurements. The synthetic grid allows for drawing most helpful shapes; it also means that the paint brush is 1x1 in synthetic grid units. These grid squares would represent 5x5ft in most tabletop games. Summary of steps below: fill a layer with ground texture, fill another layer with double-spaced synthetic grid lines, fill another layer with "Build" terrain, then use "Dig" terrain to draw walkable areas. Place props on a 4th layer (more if offset is needed).
* Install Tiled Map Editor
* Open Tiled Map Editor
* New Map
  - Set the tile size. Basically, a higher resolution is only necessary if you need **fewer** tiles per inch--if you have a more condensed map, it will use more of the pixels in a smaller area, and you don't need tiles with as many pixels each.
    For the stats below, "tpi" stands for "tiles per inch". 100 dpi, 200 dpi, etc are only in borderless form for now but make calculation easier. However, double that for gpi (grid lines per inch) since spacing is 2 tiles.
    * 100 x 100: 3/fewer tpi results in 600+ dpi (1.5/fewer tpi for 300 dpi)
      * How: Each tile contains half a grid line spacing, so you have to draw 2 in Tiled to get one grid sqare, or in other words, draw 200 pixels per grid line.
    * 64 x 64: 4.6875/fewer tpi results in 600+ dpi (2.34375/fewer tpi for 300 dpi)
    * 128 x128: 2.34375/fewer tpi results in 600+ dpi (1.171875/fewer tpi for 300 dpi)
* Open File, choose ptmk+border-64x64.tsx (or ptmk+border-128x128.tsx)
* Go back to map tab (the .tmx file)
* Make sure the "Layers" tab is selected on the right
  * IF you ever mess up your user interface (lose panels I describe in this guide), reset all your Tiled settings by deleting (/.config/mapeditor.org/tiled.conf on Linux or macOS; On Windows, the may be in %APPDATA%)
* Turn off the grid since the kit makes a special 2 unit per line grid that allows automatic cornering (Click "View," "Show Grid" unless it is already unchecked).
* Double-click the layer name and change it to **"Ground"**
  * In the "Tilesets" tab, choose a plain white square for economical printing, or choose any terrain texture you want. This will be the texture that "shows through" when you cut out the area where characters can walk.
  * Fill the entire "Ground" layer, by choosing Bucket Fill Tool (F) then clicking the background
  * Click the unlocked symbol by "Ground" layer to change it to **locked**.
* In the menu bar click "Layer," New, Tile Layer, type **"Grid"** to name it.
* Click the "Tilesets" tab at bottom right
  * Drag to select the grid (2x2 area from ID 3 to ID 20)
  * Fill the entire "Grid" layer, by choosing Bucket Fill Tool (F) then clicking the background
    * If you do not see the grid lines, try zooming in
    * If filling doesn't correctly create a grid, undo and ensure you select the whole 4x4 area in the tileset before filling.
  * Click the unlocked symbol by "Grid" layer to change it to **locked**.
* In the menu bar click Layer, New, Tile Layer, and type **"Walls"** to name it.
  * If it is mostly non-walkable, take advantage of a "Dig" terrain. Before using the Dig terrain, fill the wall layer with the solid white color. It has to the be the solid white tile for that specific terrain: Manually choose the wall material, which is the bottom left tile of the terrain, such as ID 85 for cave, or ID 80 for sharp wall--whatever is below the bottom left cutout of the tileset region (View the ID by opening the tileset in a different tab, but select the tile using the map's tab). Fill the entire layer, by choosing Bucket Fill Tool (F) then clicking the background.
  * If it is mostly walkable, you can build first. In "Terrain" tab, choose the "Build" terrain for the terrain type you want, such as "Build Sharp Wall" or "Build Cave" (make a separate layer for each so that the corners smooth automatically).
* Click the "Terrains" tab at the bottom right.
  * Choose a "Dig" terrain (or the matching "Build" to undo), and paint as needed to make your level.
    * You may have to zoom in or export to see the lines properly, otherwise it may look glitched (You may not see the continuous black outline of your cuts, which may be as narrow as 1/2 of a grid mark but should still look correct when zoomed in or exported).
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
See [github.com/poikilos/PrintableTabletopMappingKit/issues](https://github.com/poikilos/PrintableTabletopMappingKit/issues).

## Developer Notes
### Why Tileset is Inverse of Standard
I tried setting up subtractive painting in Tiled Map Editor using the normal way of doing tilesets (see terrain blocks using the Liberated Pixel Cup standard such as [LPC Terrain Repack](https://opengameart.org/content/lpc-terrain-repack)), but that did not work, even with various hacky setups in Tiled's terrain designer. I had to design all terrains with alpha opposite of normal for this to work. I could have used a ground texture with walls (see pits in LPC Terrain Repack), but then the grid would have to be embedded in every tile, making lines non-optional and tiles difficult to maintain. The inverted setup I created for Printable Tabletop Mapping Kit seems like the only way to make drawing this style of map in Tiled this easy for the user.

## License
(Author: Jake Gustafson aka poikilos)
* Data license: This work is licensed under the Creative Commons Attribution-ShareAlike 4.0 International License. To view a copy of this license, visit http://creativecommons.org/licenses/by-sa/4.0/ or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.
* Code license: no code is planned to be in this repository, but if so, see [LICENSE](https://github.com/poikilos/PrintableTabletopMappingKit/blob/master/LICENSE) for license.
