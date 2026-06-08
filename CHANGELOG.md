# Changelog

## [1.0.6] - 2026-06-08

### Added
- `Widget` component reference — drops a live "What's New" trigger into a docs page that opens your changelog (or any docs page) in a modal, the MDX counterpart to the embeddable `<script>` widget. Documents all props (`page`, `label`, `theme`, `trigger`, `width`/`height`, `radius`, `unread`, `unreadColor`, `project`, `className`), the auto-resolved `*.jamdesk.app` origin, and the per-origin unread state. Mirrors `jamdesk` build-service `<Widget>`.

## [1.0.5] - 2026-05-26

### Changed
- Upstream docs schema (`www.jamdesk.com/docs.json`) corrected its inverted `logo.light` / `logo.dark` and `favicon.light` / `favicon.dark` descriptions — the previous text claimed `light` was shown in dark mode and vice versa, which contradicted both the actual renderer and this plugin's reference. Plugin content was already accurate; no doc changes needed, but bumped to mark alignment with the corrected upstream schema.

## [1.0.4] - 2026-05-26

### Added
- `background.decoration: "none"` option to disable the jam light-mode gradient.
- `background.gradient` tuning fields (`color`, `size`, `position`, `opacity`) for parametric jam gradients. Requires `color-mix()` support; older browsers get the static jam gradient.
- Note that `background.color: { light, dark }` overrides `--color-bg-primary` on any theme.

Mirrors `jamdesk@1.1.117`.

## [1.0.3] - 2026-05-19

### Added
- `jamdesk dev --no-open` flag in the CLI command reference. `jamdesk dev` now auto-opens the docs URL in the browser while Turbopack compiles (shows the branded loading page, then auto-advances); document the opt-outs: `--no-open` per run, `"open": false` in `~/.jamdeskrc`, or `JAMDESK_NO_OPEN=1` / `CI` in the environment. Mirrors CLI `jamdesk@1.1.104`.

## [1.0.2] - 2026-05-09

### Changed
- `RequestExample` / `ResponseExample` reference: documented that bare fenced code blocks on `api:` pages render inline (not in the right-side code panel) and that the build emits an `inline_code_on_api_page` warning when wrappers are missing. Added wrong/right MDX examples mirroring the `OPENAPI.md` "Why isn't my code in the right panel?" guidance.

## [1.0.1] - 2026-04-12

### Added
- Password protection reference in configuration docs (whole-site and specific-pages modes, frontmatter `private: true`, `auth.password` config fields, mode detection rules)

## [1.0.0] - 2026-04-06

### Added
- Main skill hub with quick reference, CLI commands, writing standards
- Complete component reference (25+ components with variants)
- Full docs.json configuration schema reference
- 8 navigation patterns with decision guide
- MCP server entry for Jamdesk documentation
