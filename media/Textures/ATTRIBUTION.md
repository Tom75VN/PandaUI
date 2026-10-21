# pandaUI textures (top level)

Theme folders keep their own `ATTRIBUTION.md`. This file covers textures that
sit directly in `media/Textures/`.

- `mousewheel-zoom.tga`: World Map "wheel zooms" hint (`M.texture.mapZoomHint`,
  drawn by `modules/worldmap.lua`). Supplied by the pandaUI author on
  2026-10-20; the author generated it with ChatGPT's image model from a prompt
  written for this addon. Conversion: the 1254x1254 transparent WebP was
  cropped to its visible content, padded to a square, scaled down
  with premultiplied alpha to 64x64 and saved as an uncompressed 32-bit TGA.
  No other change to the art.
- `settings-panda-icon.tga`: round gold-rimmed panda face used as the minimap
  settings button (`M.texture.settingsIcon`, drawn by `modules/minimap.lua`).
  Supplied by the pandaUI author in chat on 2026-10-21 as a 64x64 RGBA PNG.
  Conversion: saved unchanged as an uncompressed 32-bit TGA (bottom-left
  origin, 8 alpha bits). No change to the art.
