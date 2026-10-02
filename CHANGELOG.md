# Changelog

All notable changes follow [Keep a Changelog](https://keepachangelog.com/) and
[Semantic Versioning](https://semver.org/).

## [1.1.0] - 2026-10-01

### Changed
- Default look is now white + blue tones instead of grayscale. Titles,
  bullets, rules, tables rules, listings and TikZ figures use the accent;
  blocks, notes and listings use a very light tint of it.
- `\concept` and `\arr` are colored with the accent.

### Added
- Option `palette` (`blue`, `teal`, `indigo`, `green`, `graphite`); the old gray
  look is available as `palette=graphite`.
- Option `accent` now recolors the whole theme (tints and text derive from it).
- Warm alert color (`\alert`, `alertblock`, `warnbox`, `mn alert node`).
- Environment `warnbox`; TikZ styles `mn highlight` and `mn alert node`.
- Manual slide "Palettes and color psychology".
- Contrast of accent and alert against white is >= 4.5:1 in every preset.

## [1.0.0] - 2026-10-01

### Added
- Theme `minimalist` formalized from the original ad-hoc "Sesión 5" preamble.
- Options: `accent`, `footer`, `font`, `titlerule`, `sectionpages`.
- Column environments `onecol`, `twocol`, `threecol` and `\nextcol`.
- Boxes `callout`, `statement`, `notebox` (tcolorbox based).
- `\flow`, `\flowline`, TikZ styles `mn node/arrow/dashed arrow/circle/flow`.
- Table column types `L`, `C`, `R`; `minimalist` listings style.
- Engine detection (pdfLaTeX / XeLaTeX / LuaLaTeX) via `iftex`.
- English manual (`minimalist-manual`) and Spanish example deck.
