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

- [ ] S1. Fully relaunch the client once (the probe TOC gained a file; `/reload` is not enough).
- [ ] S2. pandaUI and PandaRuntimeProbe enabled. Go where it stutters, stand still, out of combat, type `/prp puistutter`. About 2 minutes; pandaUI blinks off and on, which is expected. When chat says "results saved", type `/prp reload`.
- [ ] S3. At character select, disable pandaUI and keep PandaRuntimeProbe. Same spot, `/prp puistutter` (records the no-pandaUI reference), then `/prp reload`.
- [ ] S4. Report that both runs are done, plus any Lua error and the chat summary lines (`on ... | luaOff ... | hidden ...` and `noPandaUI ...`).

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
