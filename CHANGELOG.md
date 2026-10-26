# Changelog

Player-visible PandaUI changes, newest first. Keep every bullet short, clear and focused on what changes for the player.

## [Unreleased]

## [0.12.1] - 2026-10-26

### Added

- New option to show or hide the target-of-target frame, in the Unit Frames settings and its edit mode panel.
- Font size of the health and power bar text on unit frames can be chosen, in the Unit Frames settings and the edit mode panels.
- Health and power text on unit frames can be limited to when the cursor is over the frame.
- Power text can be set per side (default, hidden, percentage or value), in the Unit Frames settings and the unit frame edit mode panels.
- The pet frame has its own 2D/3D portrait option, in the Unit Frames settings and its edit mode panel.
- Classic-wow and modern-wow action bars have a "Slot background" option showing the Bar 1 slot plate, in ActionBars settings and edit mode.
- Classic-wow and modern-wow party frames can look like raid frames, in one column with a 30% taller power bar, in Party Frames settings and edit mode.
- Party frames have one icon size option in percent for buffs, debuffs and HoTs, raid-style included, on top of the mover scale.

### Changed

- The raid frame icon size option now sizes debuffs and dispel icons as well as HoTs.
- The action bar "Hide Slot Background" option is now "Slot border" (ticked shows the border); the edit mode bar panel drops its keybind hint.
- Addon settings categories can now provide their own mascot watermark.
- The settings pages show a new panda in the bottom-right corner.
- The modern-wow target nameplate cast bar now uses the Retail look, with spark and icon inside.
- The modern-wow pet frame text is now smaller and stays inside its bars.
- Closing an anchor's settings panel in edit mode keeps the anchor selected; click it to reopen the panel.
- The Tracked Bars edit mode "Size" slider is now "Scale (%)", like the other anchors; your size is kept.

### Fixed

- Paladins get their aura bar back, as a movable stance bar in every theme.
- Addon names and versions in the Game Settings category list now line up vertically with their icons.
- The player mana and energy tick now runs to the end of the bar at any frame scale.
- Opening Sound or Interface in Game Settings no longer shows an OptionsFrame.lua:496 error on some client versions.
- The durability readout and the damaged-armour figure now update as soon as gear is damaged.

## [0.12.0] - 2026-10-26

### Added

- Edit mode now has a Scale (%) slider for unit frames, raid, minimap, trackers and more.
- Unit frames can independently show health percentage, value or nothing on each bar side from Game Settings and Edit Mode.
- General settings now has a Font dropdown to choose the typeface of PandaUI text, with each font name shown in its own font.
- The status and online-count overlays can be switched off in Edit Mode or on a new Status overlay settings page, which also picks each status readout.
- A new Minimap settings page can group the chosen minimap icons, including other addons' buttons, behind one gear launcher icon.
- In edit mode, anchors snap to the screen centre and to other anchors' edges and centres, with a red guide line when aligned, even with Magnet off.

### Changed

- The micro bar's Size (%) slider is now named Scale (%).
- The modern-wow minimap zone name background is now one text line tall.
- Edit mode windows and their confirmation popups now use the metal frame, red close button and game settings controls in every theme.
- The modern-wow player frame name and level sit slightly higher.
- Game Settings search now finds every Video, Sound and Interface option, key binding and Panda addon option, listing only the pages with a match.

### Fixed

- Fixed the short freeze about once a minute that happened with PandaUI enabled.
- Unit frames now draw above the action bars where they overlap.
- In edit mode, cast bar anchors no longer cover the edit and anchor settings panels.
- The settings window keeps its size at any UI scale, and Panda UI pages now use the game's own settings text size.
- All sliders, including Game Settings and the colour picker, now follow the mouse as soon as you press them.
- Video, Sound and Interface settings keep the same row order and alignment when you switch pages.

## [0.11.2] - 2026-10-25

### Added

- The Pet tab now shows a clear level, loyalty, happiness and training-points summary, with a mood and diet tooltip on the happiness icon.
- Drag the pet model to rotate it, like the character model.
- Player and target frames can show class icons instead of portraits for player characters, in Blizzard or four flat styles.

### Changed

- Modern minimap zone names are smaller and fit the full width of their panel.
- Talent Advisor builds now match OctoWoW's custom talent trees.
- The Modern WoW Pet tab now groups its attributes in framed columns.
- With pandaMap installed, pandaMap now provides the world map zoom.
- Modern WoW Spellbook spell names are now white.
- Spellbook spell names now have a soft bottom-right text shadow.

### Fixed

- Modern WoW NPC windows: the NPC portrait now always sits behind the gold ring.
- Modern WoW merchant: the repair and buyback tray no longer disappears behind the footer background, and "Repair Items" is centred on the repair buttons.
- The pet experience bar now fits cleanly inside its frame.
- XP tooltip values no longer wrap onto extra lines.
- Party-frame Edit Mode handles now cover the full group at custom scale.
- Druids now get a movable form bar (Bear, Cat, Travel and more) in themes that replace the main bar.

## [0.11.1] - 2026-10-22

### Added

- A round Panda settings button now sits on the minimap rim.
- The Panda logo now appears in the settings title and watermark.

### Changed

- Every minimap icon can now be dragged around the rim.
- `/pui reset` now restores every minimap icon.

### Fixed

- Character profiles now support apostrophes and accented names.
- Existing settings carry over when a corrected character profile is created.
- Profile names may now contain apostrophes.

## [0.11.0] - 2026-10-21

### Added

- First OctoWoW release, ported from UnrealUI 0.10.2.
- Raid frames support 8 groups with healing, HoTs, debuffs and dispel highlights.
- Nameplates include reaction colours, target emphasis, raid marks and class colours.
- The minimap supports mouse-wheel zoom and a Retail-style player arrow.
- Bags recognize junk and custom OctoWoW quest items.

### Changed

- PandaUI settings now live inside OctoWoW's Game Settings window.
- The World Map no longer shows black side bands.
- Modern WoW tabs, scrollbars, buttons and thin bars now draw correctly.

### Fixed

- Game Settings sliders and dropdown layering now work correctly.
- Windowed World Map zoom no longer crashes the client.
- Quest and loot rows no longer overlap their text or artwork.
- Buffs remain where the player placed them.
- PandaQuest arrows and rare alerts keep their direction.
