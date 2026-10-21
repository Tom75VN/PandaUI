## PandaUI 0.11.0

First release of PandaUI: UnrealUI 0.10.2 ported to the **OctoWoW 1.12.1 client**, with the UnrealUI 0.11.0 nameplate options included.

* Ported to OctoWoW:
   * The whole addon now runs on the 1.12.1 client and its Lua 5.0
   * Every texture resized or repacked for the client's texture size limit
   * Settings live inside OctoWoW's own Game Settings window
   * Game Settings sliders (volume and others) now apply their value
   * Dropdown menus in the settings draw above the other controls
* New raid frames:
   * 8 groups of 5, the same design in every theme
   * Class-coloured health, power, heal prediction and your own HoTs
   * Debuffs, dispel icons and highlights
   * Preview with `/pui raid`
* Nameplate features from UnrealUI 0.11.0:
   * Colour based on the unit reaction (Hostile / Neutral / Friendly)
   * Nameplates settings: General, Health, Target, Raid Marks pages
   * Sizes, health text, target zoom and outline, fade for non-targets, raid marks, combo points, class colours, guild names and totem options
* Minimap and World Map:
   * Retail-style player arrow on the minimap and the World Map
   * Mouse-wheel zoom on the minimap
   * Black bands on each side of the World Map removed
   * Fixed a client crash when zooming the windowed World Map
* Bags:
   * Grey items are always detected for one-click junk selling
   * Custom OctoWoW quest items go to the Quest Items section
* Quests and loot:
   * Unfinished quests no longer show the yellow "?" and an active Continue button
   * Quest log button labels are no longer hidden under the button art
   * Loot rows: no more double item background, and the row fills the window
* Text keeps its chosen size with the "Original" font
* Modern WoW theme:
   * No more seam lines on the Character window tabs
   * Scrollbars, red buttons and thin bars draw correctly
* Buffs stay where you placed them
* Works with PandaQuest: its quest arrow and rare/elite alerts keep their direction

### Known issues

* Raid frames and the nameplate options are new and not yet fully tested in game.
* Some Modern WoW textures larger than 512 pixels may not draw on OctoWoW.
