# pandaUI tests to do

In-game tests still owed on OctoWoW. Tick an item once it passes. Report a
failure with its number and what you saw (exact error text if any); every
result is recorded in `knowledge.json` (`USER_CONFIRMED_INGAME`).

## URGENT: stutter with pandaUI only (reported 2026-10-25)

The client stutters with only pandaUI enabled and not with no addons. Run this
before any other test: no optimisation is attempted until it has data.

Probe: `PandaRuntimeProbe/PandaUIStutterProbe.lua`, group `puistutter`.
Knowledge records: `perf.pandaui_only_stutter`,
`api.debugprofilestop_octo_unverified`. Reading the results:
`.claude/rules/pandaui-diagnostics.md`.

- [x] S1-S4. Done 2026-10-25: the stutter is Lua garbage collection (~158 KB/s from pandaUI); tooltip, mover and status updaters fixed.
- [x] S5. Probe re-run 2026-10-25: 21 KB/s (was 158), no collection or hitch in 120 s. Still owed: confirm the freeze is gone in normal play. Re-run after the fix: `/reload` (or relaunch), pandaUI and PandaRuntimeProbe enabled, same spot, standing still, `/prp puistutter`, then `/prp reload` after "results saved". Report any Lua error, and whether the once-a-minute freeze is gone in normal play.

## Edit mode alignment guides (coded 2026-10-25, v4 confirmed in game 2026-10-26)

Code: `core/mover.lua` (`AlignDelta`, `AlignedLine`, `UpdateAlignmentGuides`).
Knowledge record: `mover.smart_alignment_guides_unverified`.

v1 failed in game (grid 20): centre X often missed, neighbour centre match drew no line. Retest v2:

- [ ] A1. `/reload`, open edit mode, grid on. Drag the player frame slowly across the screen middle: one step lands exactly on it with a red vertical line; same for the horizontal middle. Repeat with grid size 5 and 50.
- [ ] A2. Grid on, then grid off. Drag the target frame level with the player frame (top edges, then centres, then bottom edges), far apart: it snaps and a red horizontal line shows each time.
- [ ] A3. Grid on and off: line a left or right edge or the centre up with another anchor's left, right or centre: red vertical line shows.
- [ ] A4. Drag slowly through a match: the line appears only when aligned, without flicker, and disappears once past.
- [ ] A5. Grid on, away from any line: movement still steps on the grid. Report any Lua error.
- [x] A6. v2 drew centre-to-bottom but never centre-to-centre (swing bar beside cast bar). v3 still no line (2026-10-26).
- [x] A7. Trace for v3 done 2026-10-26: magnet was off, so alignment never ran (centres 0.25 apart).
- [x] A8. Confirmed fixed in game 2026-10-26. v4: `/reload`, edit mode, magnet off, grid 10. Drag the swing bar beside the cast bar: centre-to-centre snaps with a red line. Then magnet off: anchors may still overlap; magnet on: they stop at each other.

## Game Settings search (coded 2026-10-25, passed in game 2026-10-25)

Code: `modules/gamesettingslist.lua`, `modules/settings.lua`. Knowledge
record: `settings.gamesettings_search_only_open_native_leaf`.

- [x] G1. `/reload`. Esc > Options (opens on Video). Type `chat` in the search: Interface lists only its Chat sub-row, and it opens.
- [x] G2. Clear the search, open Video > Display, then type an option from another leaf (e.g. `combat text`): only matching sub-rows show, the first opens with that option.
- [x] G3. Type a Panda UI option label (e.g. `font`): Panda UI lists only pages holding it; click each, it opens. Note any hitch on the first letter typed.
- [x] G4. Type a pandaQuest and a pandaMap option label: their category lists only the matching page. Disable one addon, relaunch: its category never appears.
- [x] G5. Type `move forward`: Key Bindings is listed and its list shows that binding.
- [x] G6. `/pui` (opens on Panda UI), type a Video option: does it show? Then click Video once and retype: it must show.
- [x] G7. Clear the search: every category and sub-row returns, nothing stray drawn on any page, the game menu did not pop up.

## Nameplates: ShaguPlates options (ported 2026-10-20)

Code: `modules/nameplates.lua`, `modules/nameplatesettings.lua`,
`core/playercache.lua`. Status: `NAMEPLATES_ROADMAP.md`. Knowledge record:
`nameplates.pandaui_shaguplates_options_unverified`.

### 0. Setup

- [ ] 1. Fully relaunch the client (the TOC gained new files; `/reload` is not enough).
- [ ] 2. No Lua error at login.
- [ ] 3. Repeat the visual tests under each theme you use (modern-wow, modern, classic-wow): switch theme, `/reload`.

### 1. Settings UI

- [ ] 4. Settings shows a **Nameplates** group with four pages: General, Health, Target, Raid Marks.
- [ ] 5. No overlapping controls, and no label showing as an `NP_...` key.
- [ ] 6. The "Level font size" slider is greyed out and does not move.
- [ ] 7. Untick "Use PandaUI nameplates": a reload prompt appears, and after `/reload` the native plates are back. Tick it again, `/reload`: pandaUI plates return.

### 2. Plates (base)

- [ ] 8. Plates show name on the left, level on the right and the health bar.
- [ ] 9. Plates you are *not* targeting take their reaction colour: hostile red, neutral yellow, friendly NPC green, friendly player blue.
- [ ] 10. If every plate you aren't targeting stays red: run `/pui np` and report the `sample.barColor` line.

### 3. Visibility

- [ ] 11. Untick "Show on hostile units": enemy plates disappear. Tick it again: they return.
- [ ] 12. Tick "Show on friendly units": friendly plates appear.
- [ ] 13. After zoning or hearthing (a loading screen), both settings still apply.

### 4. Size and position (General)

- [ ] 14. Width, health bar height and vertical offset change live plates while you drag.
- [ ] 15. Name and health text font sizes change live.
- [ ] 16. After `/reload`, sizes are kept and nothing has drifted.
- [ ] 17. Untick "Show names": names hide and the level stays.
- [ ] 18. "Abbreviate long names" is on by default and shortens long names (e.g. "D. P. Captain"). Any name still over 18 characters, or a long name with the option off, ends in "...". No broken Russian or Chinese characters.

### 5. Health text (Health)

- [ ] 19. Each format works: Percent, Current, Current / Max, Current (Percent), Missing.
- [ ] 20. A creature shows real hitpoints; a player shows a percentage.
- [ ] 21. Positions Left, Center and Right work.
- [ ] 22. "Abbreviate numbers" shows 4200 as 4.2k.

### 6. Hide health bar (Health)

- [ ] 23. Hiding each category in turn (enemy NPCs, enemy players, neutral NPCs, friendly NPCs, friendly players) removes only that category's bar; name and level stay.
- [ ] 24. The bar still shows on your target and on damaged units.
- [ ] 25. Critters (rabbit, rat, deer) have no health bar by default.
- [ ] 26. Totems (needs a shaman nearby) have no health bar by default.
- [ ] 27. "Show totems as icons" draws the right icon per totem (note any blank one); the size slider works.

### 7. Target (Target)

- [ ] 28. "Fade other nameplates" and the opacity slider work.
- [ ] 29. "Enlarge the target nameplate" grows the target plate without moving it; the percentage slider works.
- [ ] 30. "Outline the target nameplate" draws an outline that follows the chosen colour; under modern-wow the selected frame takes that tint.
- [ ] 31. Reaction outlines draw each category in its reaction colour.
- [ ] 32. Where plates overlap, the target draws on top, including its bar, cast bar and debuffs.
- [ ] 33. Bags and the Character window still draw over the target plate.

### 8. Target extras

- [ ] 34. Target debuffs show above the target's plate.
- [ ] 35. A casting target shows its cast under the plate, and the standalone target castbar hides meanwhile.
- [ ] 36. Rogue or Cat Form: combo points appear under the target's bar, clear on target change, and the size slider works.
- [ ] 37. While the target casts, combo points sit under the cast bar without overlapping it.

### 9. Players (General)

- [ ] 38. An enemy player's bar is class-coloured after you target them once.
- [ ] 39. Party and guild members show friendly and class-coloured.
- [ ] 40. "Class-coloured friendly names" colours friendly player names by class.
- [ ] 41. "Show guild names": your own guild shows green, other guilds grey, guildless players show nothing.
- [ ] 42. The guild line stacks under the cast bar and above the combo points, with no overlap.
- [ ] 43. An NPC that shares a known player's name keeps its reaction colour.

### 10. Raid marks (Raid Marks)

- [ ] 44. A mark on your target shows on its plate.
- [ ] 45. Positions Left, Top and Right, the size slider and the X/Y offsets work.
- [ ] 46. A party leader marks a mob you are *not* targeting: does the mark show on its plate? This is the main unknown; report it either way.

### 11. Stability

- [ ] 47. In a crowded area (30+ plates): no stutter, no Lua errors.
- [ ] 48. Plates update correctly after zoning, dying and `/reload`.
