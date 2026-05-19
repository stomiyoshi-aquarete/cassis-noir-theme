# Cassis Noir — Project Notes

VS Code color theme published as `aquarete.cassis-noir-theme`. Deep midnight-purple base (`#2D0050`) with cassis (blackcurrant) and rose accents.

## Theme philosophy

- **Background anchor:** `editor.background` is `#2D0050` — a deep purple. Most readability tradeoffs hinge on this.
- **Hue family:** purple/magenta primary, rose accents (`#F25985`), with green and cyan as secondary signal colors.
- **Saturation rule:** UI chrome runs muted/dusky; semantic signals (diffs, errors, warnings) keep more saturation but at low alpha so text underneath stays legible.

## Diff editor coloring (`diffEditor.*`)

The deep purple background makes default VS Code diff colors look harsh — the default translucent green for inserted lines blends to a bright pink-magenta when overlaid on `#2D0050`. We override with explicit cassis-tuned values.

**Layering strategy** — each piece does one job:

| Layer | Key | Job | Current alpha |
|---|---|---|---|
| Line fill | `*.insertedLineBackground` / `*.removedLineBackground` | Broad "this block changed" cue | ~10% (`1A` / `14`) |
| Inline text fill | `*.insertedTextBackground` / `*.removedTextBackground` | Word-level highlight within a line | ~10% (`1A` / `14`) |
| Inline border | `*.insertedTextBorder` / `*.removedTextBorder` | Sharp word-level boundary | ~3% (`08`) |
| Diagonal fill | `diffEditor.diagonalFill` | Pattern in unpaired regions | ~25% (`40`) |
| Overview ruler | `diffEditorOverview.*Foreground` | Peripheral scrollbar markers | ~67% (`AA`) |

**Key principle:** a translucent fill *always* tints the text underneath. Borders don't. When boundary clarity competes with text readability, push fills lower and let borders carry the boundary cue.

**Hues (sat 70-95%):**
- Inserted (green): `#26D97A` (fills), `#46D88A` (border)
- Removed (red): `#FA5156` (fills), `#F66A6F` (border)

## Packaging

Build with `npm run package` (runs `vsce package` via `@vscode/vsce`). Output: `cassis-noir-theme-<version>.vsix` in repo root.

**`.vscodeignore` must exclude:**
- `.claude/` — personal Claude Code permission allowlist
- `.github/` — CI workflows not needed at runtime
- (plus standard `.git/`, `node_modules/`, `*.vsix`, etc.)

A v0.1.5 build leaked both before the ignore fix landed — re-check `.vscodeignore` if you add new top-level dotdirs.

## Release flow

For any color/visual change:

1. Bump `version` in [package.json](package.json) (patch for tweaks, minor for new color groups).
2. Add a `## [x.y.z]` entry to [CHANGELOG.md](CHANGELOG.md). Existing entries don't put blank lines around headings — match that style; don't reformat the whole file.
3. Commit theme + package + changelog together.
4. Push to `origin/main`.
5. `npm run package` → produces the new `.vsix`.

Marketplace publishing (`npm run publish` → `vsce publish`) is a separate manual step, not part of the standard flow yet.

## Testing color changes

1. Open this repo in VS Code, press `F5` → Extension Development Host launches with the theme loaded.
2. Open files in the host that exercise the colors you changed (diff view for `diffEditor.*`, multi-language files for token colors, etc.).
3. Theme JSON changes hot-reload — no relaunch needed.

## Current gaps (do not publish to Marketplace until resolved)

- Popular-language token coverage not verified comprehensively. Spot-check TypeScript, Python, Rust, Go, Markdown, and JSON for string interpolation, decorators, JSX/TSX attributes, and error squiggle visibility before going public.
