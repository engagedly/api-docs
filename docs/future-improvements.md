# Future improvements & references

Notes captured for later. These are **not** planned work — they're options and trade-offs to revisit when there's appetite. The current stack (Slate on Middleman 4.4, Ruby 3.4.9, deployed to GitHub Pages via GitHub Actions) works and is documented in the main [`README.md`](../README.md).

---

## 1. Make an OpenAPI spec the source of truth (highest leverage)

Today the docs are hand-authored Markdown in `source/includes/*.md`, **decoupled from the actual API**. Params, endpoints, response shapes, and error codes can drift from what `api.engagedly.com/beta` really does without anyone noticing.

Adopting an **OpenAPI 3.x spec** as the single source of truth would unlock:

- **Accuracy in CI** — validate the spec against the running API so docs can't silently drift.
- **Generated reference docs** — stop hand-syncing request/response tables.
- **Client SDK generation** and an **interactive "try it" console**.

Importantly, this is independent of the renderer — see option 3 (widdershins) for how to keep Slate while going spec-driven.

## 2. Consider a modern, actively-maintained, OpenAPI-native renderer

Slate (`slatedocs/slate`) is in low-maintenance mode, and the Ruby asset toolchain is fragile — stabilizing the recent Ruby upgrades required pinning Middleman 4.4 (not 4.5/4.6), a Sprockets `.css.scss` workaround, and dodging native-gem/clang issues. If long-term low-effort matters, evaluate:

| Tool | Open source | OpenAPI-native | "Try it" console | Notes |
|---|---|---|---|---|
| Redoc / Redocly | ✅ (core) | ✅ | Redocly (paid) | Three-panel look closest to Slate; easy drop-in |
| Scalar | ✅ | ✅ | ✅ | Modern, fast-growing, self-hostable |
| Docusaurus + OpenAPI plugin | ✅ | ✅ (plugin) | ✅ | Best if you also want guides/tutorials alongside the reference |
| Stoplight Elements | ✅ | ✅ | ✅ | Embeddable web component |
| Mintlify / ReadMe | ❌ (hosted) | ✅ | ✅ | Lowest effort, commercial, great DX |

All of these still deploy fine through the existing GitHub Actions → Pages flow (mostly static output).

## 3. If keeping Slate (lowest disruption)

Slate works today; to reduce future friction:

- **Author from OpenAPI, still render with Slate** via [`widdershins`](https://github.com/Mermade/widdershins), which converts an OpenAPI spec → Slate-flavored Markdown. Spec-driven accuracy without changing the renderer or deploy.
- **Dockerize the build** so contributors don't need the exact Ruby/bundler/clang toolchain locally (the biggest onboarding friction).
- Keep leaning on the version pins documented in the README.

## 4. Modernize icons: icon font → inline SVG (agreed — do later)

**Decision:** replace the custom icon font with inline SVGs. Not done yet; captured here for later.

**What exists today (stock Slate):**
- `font-selection.json` — an IcoMoon project file (a design/regeneration artifact; the build never reads it) defining a 4-glyph font named `slate`: `exclamation-sign`, `info-sign`, `ok-sign`, `icon-search`.
- `source/fonts/slate.{eot,ttf,woff,woff2,svg}` — the compiled webfont in 5 formats (~9 KB total).
- `source/stylesheets/_icon-font.scss` — the `@font-face` and icon classes.
- Actual usage: `aside.notice` (info-sign), `aside.warning` (exclamation-sign), and the search box (`icon-search`). `ok-sign` / `aside.success` is currently unused — so only **3 of the 4 glyphs are live**.

**Why:** the icon-font pattern is dated — superseded by inline SVG (crisper rendering, accessible, no flash-of-unstyled-text, no extra font request). Shipping a 5-format webfont (formats targeting IE ≤11 / ancient Safari) for ~3 icons is overkill in 2026.

**Plan:**
1. Add 3 inline SVGs (info, warning/exclamation, search) — as SVG partials or inlined in `layout.erb` / the aside + search markup.
2. Repoint the CSS: replace the `@font-face` glyph `:before` rules (in `_icon-font.scss` / `screen.css.scss`) for `aside.notice`, `aside.warning`, and `.search`.
3. Delete `source/fonts/`, `font-selection.json`, and `source/stylesheets/_icon-font.scss` (and its `@import`).
4. Verify: `bundle exec middleman build --clean`, then confirm the notice/warning callout icons and the search magnifier still render.

**Interim quick win (if not modernizing yet):** trim the `@font-face` to `woff2` (+ `woff`) and delete `slate.eot/.ttf/.svg` — drops 3 dead-browser formats with no real-world impact.

---

## Deferred content improvements (need real data from the API team)

From the docs review, the standard reference scaffolding already exists (authentication, requests, responses, HTTP status codes + error codes, pagination). Remaining gaps that require actual Engagedly policy/content, not guesses:

- **Rate limits** — no section today. **Tracked as "Upcoming" in [`CHANGELOG.md`](../CHANGELOG.md)** until the real throttling policy (limits, `X-RateLimit-*` headers, `429` behavior) is finalized; then add a Rate Limits section to `source/index.html.md`.
- **API changelog** — now started in [`CHANGELOG.md`](../CHANGELOG.md) (Keep a Changelog style). Consider also surfacing it *inside the docs site* as a rendered section (add a `_changelog.md` include) so API consumers see it at `api.engagedly.com/beta`.
- **Doc/API versioning** — the endpoint is `/beta`; plan a versioning story before GA (Slate handles this poorly; most modern tools in option 2 do it natively).
- **Multi-language code samples** — `language_tabs` is currently `shell` (curl) only. Options to explore:
  - **Common SDK tab sets** for API docs: Python, JavaScript/Node, Ruby, PHP, Java, Go, C#. A pragmatic starting set is **shell + Python + JavaScript** (covers the majority of API consumers).
  - **Effort caveat:** every added tab needs a sample **per endpoint** — with the current hand-authored setup that's a large, ongoing manual cost across all `source/includes/*.md`.
  - **Cheaper paths:** (a) keep shell-only and make the `curl` examples excellent; (b) go spec-driven (option 1) and **auto-generate** per-language samples from OpenAPI, which most tools in option 2 (and widdershins) do for free.
  - **Recommendation:** don't hand-add SDK tabs; decide languages only if/when official SDKs exist, and prefer generating them from a spec.
