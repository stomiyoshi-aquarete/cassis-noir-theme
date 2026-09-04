# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.8] - 2026-09-04
### Added
- `diffEditor.unchangedCodeBackground` (`#00000040`): a 25% black wash on unchanged lines so changed blocks pop against a slightly darker surround. Only takes effect when `diffEditor.hideUnchangedRegions.enabled` is on.
### Changed
- Brightened inserted/removed diff line backgrounds again, to ~20% / ~18% alpha (`33` / `2E`).

## [0.1.7] - 2026-09-04
### Changed
- Brightened inserted/removed diff line backgrounds from ~10% to ~15% alpha so changed blocks read more clearly against the deep-purple base; inline text fills and borders unchanged.

## [0.1.6] - 2026-05-19
### Changed
- Shifted removed-side diff hue from rose (341°) toward red (358°) for cleaner red/green semantic pairing on the deep-purple background.
- Quieted inserted/removed text borders to ~3% alpha so the line fill carries the boundary signal and the borders only whisper.
### Added
- `CLAUDE.md` documenting the diff editor color layering strategy, packaging conventions, and release flow.

## [0.1.5] - 2026-05-19
### Added
- Diff editor styling for the built-in differ and GitHub Pull Requests extension: inserted/removed line and inline-text backgrounds, subtle text borders, diagonal-fill for unpaired regions, and overview ruler markers — all tuned for the cassis palette so highlighted text stays readable.

## [0.1.3] - 2025-09-27
### Changed
- Rebalanced activity bar, badges, and list accents to keep navigation chrome candy-bright.
- Tweaked bracket-pair cycling and diagnostic colors for clearer nested scopes and warnings.
- Updated token hues (keywords, tags, constants, strings) to align with the warmer palette.

## [0.1.2] - 2025-09-27
### Changed
- Shifted keyword, variable, and type hues toward warmer candy tones for better differentiation in dense code blocks.

## [0.1.1] - 2025-09-27
### Changed
- Brightened activity bar foreground and refreshed key token colors for improved contrast.

## [0.1.0] - 2025-09-27
### Added
- Initial public preview of Cassis Noir (formerly Dark Purple Candy).
- Comprehensive workbench styling and terminal palette.
- Expanded TextMate token coverage with semantic highlighting enabled.
- Publishing scripts (`vsce`, `ovsx`) and project metadata.
- Repository documentation, license, and branding assets.

[0.1.3]: https://github.com/aquarete/cassis-noir-theme/releases/tag/v0.1.3
[0.1.2]: https://github.com/aquarete/cassis-noir-theme/releases/tag/v0.1.2
[0.1.1]: https://github.com/aquarete/cassis-noir-theme/releases/tag/v0.1.1
[0.1.0]: https://github.com/aquarete/cassis-noir-theme/releases/tag/v0.1.0
