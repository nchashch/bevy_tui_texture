# Changelog

### Fixed
- Glyphs rasterized in a frame whose draw payload was not extracted that
  same frame were dropped before reaching the GPU atlas and stayed
  invisible for good (e.g. text first printed after startup).
- `gpu_flush_system` is now ordered after `TerminalSystemSet::Render`
  instead of running unordered inside it, so a draw made in that set can
  no longer reach the GPU a frame late.
- Font fallback now works per cell: rows were shaped entirely with the
  font chosen for their first cell, so fonts added via
  `Fonts::add_regular_fonts` were never used past column 0.
- Glyphs from a fallback font wider than the cell width are squeezed
  horizontally to fit instead of having their right side clipped.

