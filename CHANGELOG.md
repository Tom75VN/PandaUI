# Changelog

Player-visible PandaUI changes, newest first. Keep every bullet short, clear and focused on what changes for the player.

## [Unreleased]

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
